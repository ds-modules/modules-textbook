---
interact_link: content/cp-101/lab10/lab10.ipynb
kernel_name: python3
has_widgets: false
title: 'Lab 10'
prev_page:
  url: /cp-101/lab09/lab09.html
  title: 'Lab 9'
next_page:
  url: /xenglish-r1a/xenglish-r1a-intro.html
  title: 'English'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---
{:.input_area}
```python
# Libraries that this notebook will use:
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import geopandas as gpd
from shapely.geometry import Point
# Helps the maps display nicely in the notebook:
%matplotlib inline
plt.rcParams['figure.figsize'] = [30, 20]
# Tells the notebook not to display warnings:
import warnings
warnings.filterwarnings('ignore')
```




{:.input_area}
```python
import numpy as np
import pandas as pd
```


# Working with and visualizing large datasets
- Dealing with missing values
- Filtering and selecting for certain rows and columns with ```.iloc[]``` and ```.loc[]```
- Grouping data by specific attributes with ```.groupby()```
- Working with temporal and categorial data and plotting lineplots and barplots
- Reviewing list comprehensions
- Merging two dataframes with ```.merge()```
- Plotting chloropleth maps with GeoPandas

## Data cleaning

Today we're going to extend our Pandas and Geopandas knowledge to manipulate and visualize an existing large dataset. This dataset is a random sample of tweets collected over time (2012 to 2015) in Alameda County. The most relevant columns are the tweet ID, user ID, latitude, longitude, date, and census tract number.

First, we need to clean the data. This data is relatively clean, but some columns have missing values, which may be problematic when you're trying to visualize, analyze, or model the data. There are many ways to deal with missing values, but today we're going to go over one: simply getting rid of them.

Now, let's read in the data (from a .csv file) into Pandas. We'll call the variable for the dataframe ```tweets```.



{:.input_area}
```python
tweets = pd.read_csv("tweets.csv")
tweets.head()
```


Let's take a look of how many rows we have before deleting the rows with missing values.



{:.input_area}
```python
len(tweets) ##185793
```


Let's also look at what the column names of the dataset are.



{:.input_area}
```python
tweets.columns
```


Before we clean, let's view the rows with missing values first. The code below is how we can do so. Let's break it down.

```tweets.isnull().any(axis=1)``` is a conditional statement that is a True or False value denoting if the corresponding row has a missing value.
```tweets[tweets.isnull().any(axis=1)]``` selects the rows for where the above conditional is True.

Note: axis = 0 would select the columns.

Run the code below to display the first five rows that have missing values.



{:.input_area}
```python
# Run this
# Display rows with missing values in any column.
tweets[tweets.isnull().any(axis=1)].head()
```


There should be a total of 26 rows with missing values in the dataset. Run the next cell with the len() function to confirm.



{:.input_area}
```python
len(tweets[tweets.isnull().any(axis=1)])
```


Now let's actually delete the rows, using the function 

```dataframename.dropna(axis=0, how='any')```

which drops any row where there is a missing value in any column. Use ```dropna(...)``` on the dataframe ```tweets```. Use ```len()``` to count how many rows are remaining. You should see that the row count has dropped by 81.



{:.input_area}
```python
##fill in the ...
tweets = ...
len(...)
```


Run the following cell to display the rows with missing values. There should be none.



{:.input_area}
```python
tweets[tweets.isnull().any(axis=1)]
```


Run the following cell to reset the indices and get rid of extraneous columns. We will explain how this works in a later section.



{:.input_area}
```python
tweets = tweets.reset_index()
tweets = tweets.loc[:, ['id', 'u_id', 'lat', 'lon', 'date', 'tract', 'home_tract']]
tweets.head()
```


## Plotting the number of tweets over time
### Converting to DateTime
Notice that we have temporal data in the ```tweets``` dataset. We can use the temporal information to plot the number of tweets over time. However, right now the temporal information is so fine grain, right down towards the second, that we probably won't be able to see any patterns. So for this exercise, *we only want the date information*. 

Now let's take a step backwards first.
In our dataframe, the temporal information is stored as **strings**, but for Python to understand these strings as temporal information, we'll need to convert them to **Python DateTime** objects. From then we can get the dates only.

When we run the following code, we can see that the individual dates are currently stored as strings.



{:.input_area}
```python
# Run this
print(tweets['date'][0])
print(type(tweets['date'][0]))
```


To convert them into DateTime objects, we simply need to use the 

```pd.to_datetime(<the list, array, or series you want to convert>)```

function, which outputs the converted values. In the following cell, set the date column equal to the converted values you get with ```pd._to_datetime(...)```. When you run ```print()``` lines, you should see that the type of the dates has now changed into "Timestamp".



{:.input_area}
```python
##fill in ...
tweets['date'] = ...
print(tweets['date'][0])
print(type(tweets['date'][0]))
```


Now, we want to get the date from a Timestamp, which is the first part of the output above. To do this, we will use a list comprehension.

To remind you, here's the structure of a list comprehension. Let's say you have a list called ```nums``` with values ```[1, 2, 3]``` and want to add 1 to each of the values. The variable n will take on every value in the list called nums, and then we add 1 to every value.



{:.input_area}
```python
nums = [1, 2, 3]
[n + 1 for n in nums]
```




{:.input_area}
```python
##If we wanted to do the above with a for loop, it would look like this:

nums = [1,2,3]
new_nums = []
for n in nums:
    add_1 = n + 1
    new_nums.append(add_1)
    
new_nums
```


A list comprehension runs faster than a for loop because we do everything in a single line, whereas in a for loop, we have to go through more than one line.

Now do the exercise below.

To only get the date from a Timestamp, you just need to use the function 

```<the timestamp>.date()```. 

To convert all the values in our column, we can use a list comprehension. Set the date column equal to the output of your list comprehension.

When you run the ```print()``` lines, you can see that type of the dates has now changed to "datetime.date".



{:.input_area}
```python
##fill in ...
tweets['date'] = ...
print(tweets['date'][0])
print(type(tweets['date'][0]))
```




{:.input_area}
```python
# Run this
tweets.head()
```


### Grouping tweets by date
Now we want to aggregate by date. Specifically, we want to get the count of tweets per date. We can use the function 

```<the dataframe>.groupby(by=<column name to group by>).<an aggregating function, e.g. count(), max(), mean()>```, 

which outputs a grouped dataframe, to do so. Which aggregating function should we use? Set a variable called ```tweets_by_date``` equal to the grouped dataframe. 



{:.input_area}
```python
##fill in ...
tweets_by_date = ...
tweets_by_date.head()
```


Below, we are going to perform some dataframe operations that will prepare our data for visualization. Pay attention, as you will need to do something similar later on.

Notice how the date column is now bolded. Pandas now views the date column as an index, which is like an address. However, we want it to be a normal column again if we want to access it with attributes like ```loc``` and ```iloc```. We use ```reset_index()``` to reset the index.



{:.input_area}
```python
# Run this
tweets_by_date = tweets_by_date.reset_index()
tweets_by_date.head()
```


Now we have a lot of columns that we don't need. Remember ```.iloc[]```? We'll use ```.iloc[]``` to select only the first two columns.



{:.input_area}
```python
# Run this
tweets_by_date = tweets_by_date.iloc[:, 0:2]
tweets_by_date.head()
```


The second column has a weird name. ```tweets_by_date.columns``` gets the column names of the dataframe. We can set them equal to a list with the new column names to rename them. Let's run the cell below to rename the id column to number of tweets



{:.input_area}
```python
# Run this
tweets_by_date.columns = ['date', 'number of tweets']
tweets_by_date.head()
```


### Using Matplotlib to plot a line plot: Number of tweets vs. date
Time to plot! Use 

```plt.plot(<list, array, or series of the x values>, <the y values>)```

to plot the number of tweets vs. time. We've labeled the axes and title. Study the code, as you will need to do it yourself later. 



{:.input_area}
```python
##fill in the ... with your plotting code
plt.figure(figsize=[18, 7])
...
plt.xlabel('time')
plt.ylabel('number of tweets')
plt.title('Number of Tweets over Time')
```


## Number of tweets by tract - Barplots
### Grouping tweets by census tract
Remember how we grouped tweets by date? Do the same, but this time, group instead by ```tract``` and aggregate with count(). Set the output equal to a variable called ```tweets_by_tract```.



{:.input_area}
```python
##fill in the ...
tweets_by_tract = ...
tweets_by_tract.head()
```


Pandas now sees the tract as an index, but we don't want that. Set the indices back to normal using ```reset_index()```, referencing the previous section.



{:.input_area}
```python
##fill in the ...
tweets_by_tract = ...
tweets_by_tract.head()
```


We only want the tract number and counts. Use ```.iloc[]``` to select only the first two columns.



{:.input_area}
```python
##fill in the ...
tweets_by_tract = ...
tweets_by_tract.head()
```



Now we want to rename this ```id``` column to ```number of tweets```. Can you recall from the previous section how to do that?



{:.input_area}
```python
##fill in the ...
tweets_by_tract.columns = ...
tweets_by_tract.head()
```


### Sorting tweet counts in descending order
There are 360 tracts, which is too much to plot on one bar plot. Let's graph the top 10 tracts with the most tweets. 

First, let's set ```tweets_by_tract``` to a sorted version of itself. Use the function:

```<the dataframe>.sort_values(by=<column name>, ascending=False)```

which outputs a sorted dataframe, to do so.



{:.input_area}
```python
##fill in the ...
tweets_by_tract = ...
tweets_by_tract.head()
```


Note: ascending = False makes it so that we sort the number of tweets in descending order. ascending = True will sort them in ascending order.

### Convert census tract numbers to strings
Currently, the census tracts are stored as integers. If you tried to plot with these, the barplot would not display correctly. Additionally, census tracts are not numerical data, but categorical data. So, instead we want to store each census tract as a **string**. We can use a list comprehension to do so!

Create a new column in ```tweets_by_tract``` named ```GEOID``` with these census tract strings.

*Important Hint:*
Make sure that the strings are of a specific format.
The tract numbers are currently of the **float** type, which means they have decimal points (e.g. 10.0). We want them to be **integers** (e.g. 10) before we convert them into strings.

You can use ```int()``` to convert a float first to an integer. Then use ```str()``` to convert the integer into a string! To do both at once, use ```str(int(...))```.



{:.input_area}
```python
##fill in the ...
tweets_by_tract['GEOID'] = ...
tweets_by_tract.head()
```


Now we want to plot the top 10 tracts with the highest counts. Use ```.iloc[]```to select the top 10 GEOID's and the top 10 tweet counts. Remember: columns have indices starting at 0! Which index are the GEOID and number of tweets columns in? After this, use

```plt.bar(<the list, array, or series of x values>, <the y values>)```

to plot a bar plot (note: if we want a horizontal bar plot, simply add an 'h' after bar. But for this, we will get vertical bars instead). Make sure to add a labels to the x and y axes, as well as the title. Refer to the previous section for how to do so.



{:.input_area}
```python
##fill in the ...
top_10_tracts = ...
top_10_tweetcounts = ...
plt.figure(figsize=[18, 10])
...
...
...
...
```


## Moving on to GeoPandas: Visualizing number of tweets per census tract spatially
The bar plot is fascinating, but we're not any more enlightened than before, because most people don't memorize census tract numbers. A better way would be to analyze the data spatially, which means using GeoPandas!

Read in the alameda data from the previous lab. This contains the Shapely geometry polygons that we'll need to map our data.



{:.input_area}
```python
alameda = gpd.read_file('alameda_shapefiles')
alameda.head()
```


Let's recall what the column names are for this dataset. Run the cell below.



{:.input_area}
```python
alameda.columns
```


We don't need all of these columns. Use ```.loc[]``` to select only the columns named:
GEOID, female, male, medianage, total_pop, and geometry.



{:.input_area}
```python
alameda = alameda.loc[:, ['GEOID', 'female', 'male', 'medianage', 'total_pop', 'geometry']]
alameda.head()
```


### Merging dataframes
Notice how the ```alameda``` dataset contains a variety of values by GEOID. Conveniently, so does our ```tweets_per_tract``` dataset! If we simply add the tweet counts to the alameda dataset, we would be able to plot a chloropleth map on the number of tweets per census tract.

To do so, we're going to perform an operation called a **merge** or **join**. We're going to perform the join on the ```GEOID``` column, so that the tweet count data corresponds correctly to the right census tract.

First, we need to fix a slight problem. The ```alameda GEOID``` column values have a 0 before, while the ```tweets_by_tract GEOID``` column values don't. This is easy, we can just concatenate a '0' in front of each census tract number in ```tweets_by_tract``` using a list comprehension.

Below is a quick review on how string concatenation works.



{:.input_area}
```python
"pineapple" + "pen"
```


Now, fill in the cell below with a list comprehension that append a '0' in f ront of each GEOID.

Hint: recall the str(int()) trick from before.



{:.input_area}
```python
##fill in the ...
tweets_by_tract['GEOID'] = ...
tweets_by_tract.head()
```


Time to merge! Use the function

```<a dataframe>.merge(<another dataframe>, on=<column name to merge on>)```

and set the output equal to variable called ```combined```.



{:.input_area}
```python
##fill in
combined = ...
combined.head()
```


There are other types of merging techniques in python. By default, if we do not specify what type of merge we do, python will treat is as a ```left``` join, which means if will keep all the unique values for the table on the left of the .merge method. To learn more about other types of joins, see the link below:

https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.join.html


Recall the chloropleths we created in the last lab. Now create a chloropleth map of the number of tweets per census tract.

Reference:
```<the geodataframe>.plot(column=<column name>, legend=True, figsize=[18, 10])```

Remember to add a title and remove the axes.



{:.input_area}
```python
#fill in the ... with your code and replace the next line with combined.plot(...)

##replace this line with combined.plot(...)
bounds = ...
minx = bounds[0]
miny = bounds[1]
maxx = bounds[2]
maxy = bounds[3]
text_properties = {'ha': 'center', 'va': 'center', 'fontsize' : 20} 
plt.text(maxx + (maxx-minx)/4.5, (maxy - miny)/2 + miny, 'Percentage of Tweet Counts by Census Tract', text_properties, rotation=90)
plt.title(..., fontsize = 30)
plt.axis(..);
```


This looks so much better than the bar plot! But what if some census tracts only have a lot of tweets because they have a larger population size? Instead, we should plot number of tweets per capita.

Make a new column in ```combined``` called ```avg tweets per capita```. Set it equal to ```number of tweets``` divided by ```total_pop```. Then plot the new chloropleth map. Remember to add the title and remove the axes.



{:.input_area}
```python
##fill in the ... with your code
combined["avg tweets per capita"] = ...

##Let's see what the table looks now with the new column:
combined.head() ##scroll to the right if needed to see all the columns
```




{:.input_area}
```python
##fill in the ... with your code to plot
combined.plot(...)
plt.text(maxx + (maxx-minx)/4.5, (maxy - miny)/2 + miny, 'Percentage of Tweet Counts by Census Tract', text_properties, rotation=90)
plt.title(...)
plt.axis(...);
```


These are by no means the only visualizations you can create with the ```combined``` dataset. In the cell below, create your own visualization! 



{:.input_area}
```python
# Your own visualization here
```


## Feedback form
Thank you for exploring data science with us! We hope you have enjoyed the past four labs that the division of data science has created for you. It would be wonderful if you could leave us feedback here so that we can improve for the course in the future:

https://docs.google.com/forms/d/e/1FAIpQLSe54U3E64kYFWwQHSUpAvWYMuJOdKzbHDZjPa3nMUlHSSs0PQ/viewform


## Resources
If you're interested in exploring more about data science, Berkeley's [Data 8](https://www.inferentialthinking.com/chapters/intro.html) and [Data 100](https://www.textbook.ds100.org/) textbooks are very well-written with interactive links to follow along.

There are also websites like [DataCamp](https://www.datacamp.com/courses) and [DataQuest](https://www.dataquest.io/course/python-for-data-science-fundamentals/) that offer online interactive courses in R, Python, and SQL, many of them for free.

If you're stuck trying to work on a project, [Data Peer Consulting](https://data.berkeley.edu/education/data-peer-consulting) at the Division of Data Sciences could be helpful to you.

If you're looking for more specialized help, the [D-lab](https://dlab.berkeley.edu/) which focuses on data science applications to the social sciences specifically, holds [workshops](https://dlab.berkeley.edu/training) and [consulting](https://dlab.berkeley.edu/consulting), many on geospatial data.

---
### Author: Rebekah Tang

### References:
- GeoPandas Mapping Documentation: http://geopandas.org/mapping.html
- Pandas Documentation: https://pandas.pydata.org/pandas-docs/stable/reference/frame.html
- Matplotlib Documentation: https://matplotlib.org/api/pyplot_summary.html
