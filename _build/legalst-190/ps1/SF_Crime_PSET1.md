---
redirect_from:
  - "/legalst-190/ps1/sf-crime-pset1"
interact_link: content/legalst-190/ps1/SF_Crime_PSET1.ipynb
kernel_name: python3
title: 'Problem Set 1'
prev_page:
  url: /legalst-190/1-18
  title: 'Intro to Python'
next_page:
  url: /psych-167ac/psych-167ac-intro
  title: 'Psychology'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---

# SF Crime PSET 1

1. [Introduction](#intro)
2. [Getting the Data](#data)
3. [Descriptive Statistics](#stats)
4. [Geographic Information Systems](#gis)
5. [Discussion Questions](#dq)



{:.input_area}
```python
# imports
import requests
from datascience import *
import matplotlib.pyplot as plt
import datetime
import folium
from folium import GeoJson
import time
import json
import os
from branca.colormap import linear
import branca.colormap
import pandas as pd
%matplotlib inline
```


## 1. Introduction <a id='intro'></a>

For this lab, we will be working with the San Francisco Police Department's Incident Database. The dataset contains up-to-date information on incidents reported to the SFPD. Each observation is tagged with information about the incident's location, type of infraaction, and date/time. In this lab you will:

1. Download the data through an Application Programming Interface (API)
2. Explore the data with summary and descriptive statistics
3. Map the incidents

Make sure to start early and ask lots of questions! The dataset, along with other publicaly available data, is available at: https://data.sfgov.org/Public-Safety/Police-Department-Incidents/tmnf-yvry

## 2. Getting the Data <a id='data'></a>

Write code that pulls the data into your environment with an API call. Here is the link to the API: https://data.sfgov.org/resource/PdId.json



{:.input_area}
```python
os.path.
```




{:.input_area}
```python
sf_police = os.path.join('Police_Department_Sample_Incidents.csv')
df = pd.read_csv(sf_police)
```




{:.input_area}
```python
# the url that we want to get our data from
#
#  ******* THIS IS THE OLD DATA PULLING CELL. DO NOT USE. USE CELL BELOW. *******
data_url = 'https://data.sfgov.org/resource/PdId.json?$limit=1&$offset=0&$order=date DESC'

# making our http request to DATA_URL
response = requests.get(data_url)
# using the built-in json decoder of the requests library to interpret the text
json_response = response.json()
len(json_response)
```




{:.input_area}
```python
#ts = Table(data.labels)
offset = 0
n = 2
recs = []
while n > 0:
    print(n)
    lnk = 'https://data.sfgov.org/resource/PdId.json?$limit=50000&$offset={}&$order=date DESC'.format(str(offset))
    r = requests.get(lnk)
    js = r.json()
    recs.extend(js)
    offset += 50000
    n -= 1
len(recs)
```




{:.input_area}
```python
import pandas as pd
df = pd.DataFrame(recs)
df.head()
```




{:.input_area}
```python
data = Table.from_df(df.drop('location', axis=1))
data
```




{:.input_area}
```python
min(df['date'])
```




{:.input_area}
```python
# making a table out of our json
# DO NOT USE 
#data = Table.from_records(json_response)
#data.show(3)
```




{:.input_area}
```python
data['y'] = data['y'].astype('float')
data['x'] = data['x'].astype('float')
```


**QUESTION: What are the advantages to downloading data this way, instead of with a point-and-click action?**

## 3. Descriptive Statistics <a id='stats'></a>

Plot the number of incidents per year from 2000-2017 (choose the appropriate type of plot). Have crime rates increased or decreased in general? 



{:.input_area}
```python
# creating a year column from the first four characters of the 'date' column
data['year'] = pd.DatetimeIndex(df['date']).year
data
```




{:.input_area}
```python
agg_on_year = data.group('year')
agg_on_year.show()
```




{:.input_area}
```python
agg_on_year.plot('year', 'count')
```


Looking just at 2017, what proportion of the total does each type of crime constitute? Use at least one table and at least one plot to support your answer.



{:.input_area}
```python
agg_by_crime = data.where('year', 2017).group('category')
agg_by_crime['proportion'] = [count / sum(agg_by_crime.column('count')) for count in agg_by_crime.column('count')]
agg_by_crime.sort('proportion', descending=True)
```




{:.input_area}
```python
agg_by_crime.sort('count', descending=True).barh('category', 'proportion')
```


Is there a relationship between day of week, time, and whether an incident occurs? Bonus: Is there a relationship between day/time and particular types of incidents?



{:.input_area}
```python
data.group('dayofweek').barh('dayofweek')
```




{:.input_area}
```python
# making an hour column that can be grouped on
data['hour'] = [int(t[:2]) for t in data['time']]
```




{:.input_area}
```python
data.group('hour').bar('hour')
```


#### Bonus: Are there any other interesting relationships in the data?

# 4. Geographic Information Systems (GIS) <a id='gis'></a>

Plot individual incidents in 2017 as points on a map of San Francisco. Does crime seem randomly distributed in space, or do incidents tend to cluster close together? Propose an explanation for your conclusion. Bonus: Shade the points by type of crime.

Hint: Use the `basemap` extension to the `matplotlib` package!



{:.input_area}
```python
twentyeighteen = data.where('year' == 2017).sample(1000)
twentyeighteen['y'] = twentyeighteen['y'].astype('float')
twentyeighteen['x'] = twentyeighteen['x'].astype('float')
```




{:.input_area}
```python
mp = folium.Map(location=[37.7749, -122.4194])
for coords in list(zip(twentyeighteen['y'], twentyeighteen['x'])):
    folium.Marker(
        location=coords
    ).add_to(mp)
mp
```




{:.input_area}
```python
from folium.plugins import HeatMap

mp = folium.Map(location=[37.7749, -122.4194])
HeatMap(list(zip(twentyeighteen['y'], twentyeighteen['x']))).add_to(mp)
mp
```


Merge the incidents data with either a Shapefile or GeoJSON file with information on the boundaries of neighborhoods in San Francisco. 

The neighborhood data is available here: https://data.sfgov.org/Geographic-Locations-and-Boundaries/Analysis-Neighborhoods/p5b7-5n3h

The API endpoint: https://data.sfgov.org/resource/xfcw-9evu.json

*.geojson



{:.input_area}
```python
#import requests
#r = requests.get(url='https://data.sfgov.org/resource/xfcw-9evu.json')
```




{:.input_area}
```python
sf_neighborhoods = os.path.join('SF Find Neighborhoods.geojson')
geo_json_data = json.load(open(sf_neighborhoods))
```




{:.input_area}
```python
m = folium.Map([37.7749, -122.4194], zoom_start = 12)
m
```




{:.input_area}
```python
# might be too big bc won't display
m = folium.Map(
    location=[37.7749, -122.4194], zoom_start = 12
)

folium.GeoJson(geo_json_data
).add_to(m)
m
```


Construct a choropleth map, coloring in each neighborhood by how many incidents it had in 2018. Bonus: Construct several maps that explore differences by day of week, time of year, time of day, etc.



{:.input_area}
```python
twentyeighteen = twentyeighteen.to_df()
```




{:.input_area}
```python
import geopandas as gpd
import shapely
shapely.speedups.enable()
```




{:.input_area}
```python
twentyeighteen_spatial_points = gpd.GeoDataFrame(twentyeighteen.drop(['x', 'y'], axis=1),
                       crs={'init': 'epsg:4326'},
                       geometry=twentyeighteen.apply(lambda row: shapely.geometry.Point((row.x, row.y)), axis=1))
```




{:.input_area}
```python
sf_polygons = gpd.GeoDataFrame.from_features(geo_json_data['features'])
sf_polygons.crs = {'init' :'epsg:4326'}
```




{:.input_area}
```python
sf_spatial = gpd.sjoin(sf_polygons, twentyeighteen_spatial_points, how="inner", op="intersects")
```




{:.input_area}
```python
crime_neighborhood = pd.DataFrame(sf_spatial).reset_index()
crime_neighborhood.head(5)
```




{:.input_area}
```python
crime_neighborhood_agg = crime_neighborhood.groupby('name').size().reset_index()
crime_neighborhood_agg.head(5)
```




{:.input_area}
```python
crime_neighborhood_agg.columns = ['neighborhood', 'crimes']
crime_neighborhood_agg.head(5)
```


Do you notice any patters? Are there particular neighborhoods where crime concentrates more heavily?



{:.input_area}
```python
m = folium.Map(
    location=[37.7749, -122.4194], zoom_start = 12
)

m.choropleth(
    geo_data=geo_json_data,
    data=crime_neighborhood_agg,
    columns=['neighborhood', 'crimes'],
    key_on='feature.properties.name',
    fill_color='OrRd',
    threshold_scale=[10, 60, 100, 140],
    highlight=True
    )

m
```


# 5. Discussion Questions <a id='dq'></a>

Based on the evidence from this lab assignment, why do you think "hot spots" policing became more popular in the last few decades? What are the pros and cons to this kind of approach?

What other sorts of data would help improve your analysis?



{:.input_area}
```python
def append_and_follow(t, link, n):
    if n == 0:
        print('Next link (if you want to continue)', link)
        return t
    time.sleep(3)
    print(n)
    r = requests.get(link)
    js = r.json()
    return append_and_follow(t.append(Table.from_records(js['value'])), js['@odata.nextLink'], n-1)

starter = Table(('__id', 'address', 'category', 'date', 'dayofweek', 'descript', 'incidntnum', 
                 'location', 'pddistrict', 'pdid', 'resolution', 'time', 'x', 'y'))
starting_url = 'https://data.sfgov.org/api/odata/v4/tmnf-yvry'

c = append_and_follow(starter, starting_url, 6)
c
```

