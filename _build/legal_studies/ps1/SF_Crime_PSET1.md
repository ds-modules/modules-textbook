---
redirect_from:
  - "/legal-studies/ps1/sf-crime-pset1"
interact_link: content/legal_studies/ps1/SF_Crime_PSET1.ipynb
kernel_name: python3
has_widgets: false
title: 'Problem Set 1'
prev_page:
  url: /legal_studies/1-18.html
  title: 'Intro to Python'
next_page:
  url: 
  title: ''
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
sf_police = os.path.join('Police_Department_Sample_Incidents.csv')
df = pd.read_csv(sf_police)
df
```





<div markdown="0" class="output output_html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>incidntnum</th>
      <th>category</th>
      <th>descript</th>
      <th>dayofweek</th>
      <th>date</th>
      <th>time</th>
      <th>pddistrict</th>
      <th>resolution</th>
      <th>address</th>
      <th>x</th>
      <th>y</th>
      <th>location</th>
      <th>pdid</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>30325834</td>
      <td>OTHER OFFENSES</td>
      <td>POSSESSION OF BURGLARY TOOLS</td>
      <td>Wednesday</td>
      <td>03/19/2003</td>
      <td>01:06:00</td>
      <td>MISSION</td>
      <td>ARREST, BOOKED</td>
      <td>3100 Block of CESAR CHAVEZ ST</td>
      <td>-122.412594</td>
      <td>37.748166</td>
      <td>(37.7481660056223, -122.412594354828)</td>
      <td>3.032583e+12</td>
    </tr>
    <tr>
      <th>1</th>
      <td>150119979</td>
      <td>OTHER OFFENSES</td>
      <td>TRAFFIC VIOLATION</td>
      <td>Sunday</td>
      <td>02/08/2015</td>
      <td>03:26:00</td>
      <td>INGLESIDE</td>
      <td>ARREST, BOOKED</td>
      <td>MISSION ST / COLLEGE AV</td>
      <td>-122.424702</td>
      <td>37.735370</td>
      <td>(37.7353699090873, -122.424702079332)</td>
      <td>1.501200e+13</td>
    </tr>
    <tr>
      <th>2</th>
      <td>130507219</td>
      <td>OTHER OFFENSES</td>
      <td>RESISTING ARREST</td>
      <td>Thursday</td>
      <td>06/20/2013</td>
      <td>15:22:00</td>
      <td>CENTRAL</td>
      <td>ARREST, CITED</td>
      <td>200 Block of SACRAMENTO ST</td>
      <td>-122.398405</td>
      <td>37.794412</td>
      <td>(37.7944120086129, -122.39840549202)</td>
      <td>1.305072e+13</td>
    </tr>
    <tr>
      <th>3</th>
      <td>40459865</td>
      <td>OTHER OFFENSES</td>
      <td>LOST/STOLEN LICENSE PLATE</td>
      <td>Wednesday</td>
      <td>04/21/2004</td>
      <td>11:00:00</td>
      <td>INGLESIDE</td>
      <td>NONE</td>
      <td>600 Block of 28TH ST</td>
      <td>-122.436797</td>
      <td>37.744751</td>
      <td>(37.7447510901057, -122.436796627403)</td>
      <td>4.045987e+12</td>
    </tr>
    <tr>
      <th>4</th>
      <td>70067529</td>
      <td>FORGERY/COUNTERFEITING</td>
      <td>CHECKS, MAKE OR PASS FICTITIOUS</td>
      <td>Friday</td>
      <td>01/05/2007</td>
      <td>12:00:00</td>
      <td>INGLESIDE</td>
      <td>NONE</td>
      <td>1600 Block of BURROWS ST</td>
      <td>-122.419412</td>
      <td>37.724888</td>
      <td>(37.7248875198607, -122.41941248624)</td>
      <td>7.006753e+12</td>
    </tr>
    <tr>
      <th>5</th>
      <td>106103162</td>
      <td>LARCENY/THEFT</td>
      <td>PETTY THEFT OF PROPERTY</td>
      <td>Thursday</td>
      <td>08/19/2010</td>
      <td>14:05:00</td>
      <td>BAYVIEW</td>
      <td>NONE</td>
      <td>1300 Block of REVERE AV</td>
      <td>-122.385545</td>
      <td>37.728980</td>
      <td>(37.728979731984, -122.385545453301)</td>
      <td>1.061032e+13</td>
    </tr>
    <tr>
      <th>6</th>
      <td>120276214</td>
      <td>ASSAULT</td>
      <td>BATTERY WITH SERIOUS INJURIES</td>
      <td>Saturday</td>
      <td>04/07/2012</td>
      <td>03:05:00</td>
      <td>PARK</td>
      <td>ARREST, BOOKED</td>
      <td>500 Block of CENTRAL AV</td>
      <td>-122.444569</td>
      <td>37.774618</td>
      <td>(37.7746181158166, -122.444568876114)</td>
      <td>1.202762e+13</td>
    </tr>
    <tr>
      <th>7</th>
      <td>170096642</td>
      <td>LARCENY/THEFT</td>
      <td>PETTY THEFT SHOPLIFTING</td>
      <td>Friday</td>
      <td>02/03/2017</td>
      <td>15:00:00</td>
      <td>MISSION</td>
      <td>NONE</td>
      <td>400 Block of CASTRO ST</td>
      <td>-122.435150</td>
      <td>37.761760</td>
      <td>(37.761759724359806, -122.43515009981229)</td>
      <td>1.700966e+13</td>
    </tr>
    <tr>
      <th>8</th>
      <td>40822096</td>
      <td>OTHER OFFENSES</td>
      <td>DRIVERS LICENSE, SUSPENDED OR REVOKED</td>
      <td>Monday</td>
      <td>07/19/2004</td>
      <td>13:00:00</td>
      <td>TENDERLOIN</td>
      <td>ARREST, CITED</td>
      <td>EDDY ST / HYDE ST</td>
      <td>-122.415885</td>
      <td>37.783516</td>
      <td>(37.7835160563924, -122.415885065795)</td>
      <td>4.082210e+12</td>
    </tr>
    <tr>
      <th>9</th>
      <td>100487776</td>
      <td>LARCENY/THEFT</td>
      <td>PETTY THEFT FROM A BUILDING</td>
      <td>Friday</td>
      <td>05/07/2010</td>
      <td>20:30:00</td>
      <td>SOUTHERN</td>
      <td>NONE</td>
      <td>400 Block of MINNA ST</td>
      <td>-122.407387</td>
      <td>37.781069</td>
      <td>(37.7810688918781, -122.407387172098)</td>
      <td>1.004878e+13</td>
    </tr>
    <tr>
      <th>10</th>
      <td>160459555</td>
      <td>ROBBERY</td>
      <td>ROBBERY OF A SERVICE STATION WITH A GUN</td>
      <td>Sunday</td>
      <td>06/05/2016</td>
      <td>18:35:00</td>
      <td>TARAVAL</td>
      <td>NONE</td>
      <td>1100 Block of JUNIPERO SERRA BL</td>
      <td>-122.472389</td>
      <td>37.717501</td>
      <td>(37.7175010456614, -122.4723890410333)</td>
      <td>1.604596e+13</td>
    </tr>
    <tr>
      <th>11</th>
      <td>120107590</td>
      <td>LARCENY/THEFT</td>
      <td>GRAND THEFT BICYCLE</td>
      <td>Friday</td>
      <td>02/03/2012</td>
      <td>19:00:00</td>
      <td>RICHMOND</td>
      <td>NONE</td>
      <td>600 Block of 25TH AV</td>
      <td>-122.484596</td>
      <td>37.777213</td>
      <td>(37.7772129804302, -122.484595739169)</td>
      <td>1.201076e+13</td>
    </tr>
    <tr>
      <th>12</th>
      <td>100847910</td>
      <td>VANDALISM</td>
      <td>MALICIOUS MISCHIEF, VANDALISM</td>
      <td>Monday</td>
      <td>09/13/2010</td>
      <td>00:01:00</td>
      <td>MISSION</td>
      <td>NONE</td>
      <td>100 Block of GRANDVIEW AV</td>
      <td>-122.440412</td>
      <td>37.755446</td>
      <td>(37.7554456064661, -122.440411847156)</td>
      <td>1.008479e+13</td>
    </tr>
    <tr>
      <th>13</th>
      <td>30802688</td>
      <td>LARCENY/THEFT</td>
      <td>PETTY THEFT FROM LOCKED AUTO</td>
      <td>Saturday</td>
      <td>07/05/2003</td>
      <td>16:00:00</td>
      <td>NORTHERN</td>
      <td>NONE</td>
      <td>FRANKLIN ST / ELLIS ST</td>
      <td>-122.422654</td>
      <td>37.783620</td>
      <td>(37.7836201224122, -122.422654162991)</td>
      <td>3.080269e+12</td>
    </tr>
    <tr>
      <th>14</th>
      <td>60098528</td>
      <td>NON-CRIMINAL</td>
      <td>TARASOFF REPORT</td>
      <td>Thursday</td>
      <td>01/26/2006</td>
      <td>09:15:00</td>
      <td>TENDERLOIN</td>
      <td>NONE</td>
      <td>300 Block of EDDY ST</td>
      <td>-122.413791</td>
      <td>37.783837</td>
      <td>(37.7838365565348, -122.413790972781)</td>
      <td>6.009853e+12</td>
    </tr>
    <tr>
      <th>15</th>
      <td>130149833</td>
      <td>MISSING PERSON</td>
      <td>MISSING JUVENILE</td>
      <td>Wednesday</td>
      <td>02/20/2013</td>
      <td>09:00:00</td>
      <td>PARK</td>
      <td>LOCATED</td>
      <td>100 Block of BELVEDERE ST</td>
      <td>-122.449329</td>
      <td>37.767774</td>
      <td>(37.7677738874748, -122.449328648219)</td>
      <td>1.301498e+13</td>
    </tr>
    <tr>
      <th>16</th>
      <td>41322974</td>
      <td>LARCENY/THEFT</td>
      <td>GRAND THEFT FROM A BUILDING</td>
      <td>Thursday</td>
      <td>11/18/2004</td>
      <td>17:00:00</td>
      <td>CENTRAL</td>
      <td>NONE</td>
      <td>900 Block of MASON ST</td>
      <td>-122.410846</td>
      <td>37.792316</td>
      <td>(37.7923158747647, -122.410845624227)</td>
      <td>4.132297e+12</td>
    </tr>
    <tr>
      <th>17</th>
      <td>100174597</td>
      <td>LARCENY/THEFT</td>
      <td>PETTY THEFT SHOPLIFTING</td>
      <td>Sunday</td>
      <td>02/21/2010</td>
      <td>17:20:00</td>
      <td>SOUTHERN</td>
      <td>ARREST, CITED</td>
      <td>800 Block of MARKET ST</td>
      <td>-122.407634</td>
      <td>37.784189</td>
      <td>(37.7841893501425, -122.407633520742)</td>
      <td>1.001746e+13</td>
    </tr>
    <tr>
      <th>18</th>
      <td>130034347</td>
      <td>OTHER OFFENSES</td>
      <td>CONSPIRACY</td>
      <td>Sunday</td>
      <td>01/13/2013</td>
      <td>01:03:00</td>
      <td>TENDERLOIN</td>
      <td>ARREST, BOOKED</td>
      <td>100 Block of ELLIS ST</td>
      <td>-122.408271</td>
      <td>37.785494</td>
      <td>(37.7854941424186, -122.408270724034)</td>
      <td>1.300343e+13</td>
    </tr>
    <tr>
      <th>19</th>
      <td>150034220</td>
      <td>VEHICLE THEFT</td>
      <td>STOLEN AUTOMOBILE</td>
      <td>Sunday</td>
      <td>01/11/2015</td>
      <td>23:00:00</td>
      <td>INGLESIDE</td>
      <td>NONE</td>
      <td>1200 Block of ALEMANY BL</td>
      <td>-122.432269</td>
      <td>37.730139</td>
      <td>(37.7301394309025, -122.432268894425)</td>
      <td>1.500342e+13</td>
    </tr>
    <tr>
      <th>20</th>
      <td>101033821</td>
      <td>DRUG/NARCOTIC</td>
      <td>POSSESSION OF BASE/ROCK COCAINE FOR SALE</td>
      <td>Saturday</td>
      <td>11/06/2010</td>
      <td>22:00:00</td>
      <td>TENDERLOIN</td>
      <td>ARREST, BOOKED</td>
      <td>OFARRELL ST / JONES ST</td>
      <td>-122.412971</td>
      <td>37.785788</td>
      <td>(37.7857883766888, -122.412970537591)</td>
      <td>1.010338e+13</td>
    </tr>
    <tr>
      <th>21</th>
      <td>130473234</td>
      <td>SUSPICIOUS OCC</td>
      <td>SUSPICIOUS OCCURRENCE</td>
      <td>Saturday</td>
      <td>06/08/2013</td>
      <td>18:00:00</td>
      <td>RICHMOND</td>
      <td>UNFOUNDED</td>
      <td>300 Block of 7TH AV</td>
      <td>-122.465490</td>
      <td>37.781907</td>
      <td>(37.7819066124774, -122.465490381382)</td>
      <td>1.304732e+13</td>
    </tr>
    <tr>
      <th>22</th>
      <td>96024454</td>
      <td>LARCENY/THEFT</td>
      <td>GRAND THEFT FROM LOCKED AUTO</td>
      <td>Monday</td>
      <td>04/06/2009</td>
      <td>14:30:00</td>
      <td>INGLESIDE</td>
      <td>NONE</td>
      <td>1500 Block of TREAT AV</td>
      <td>-122.412506</td>
      <td>37.745680</td>
      <td>(37.7456802881475, -122.41250614556)</td>
      <td>9.602445e+12</td>
    </tr>
    <tr>
      <th>23</th>
      <td>70430788</td>
      <td>LARCENY/THEFT</td>
      <td>GRAND THEFT FROM PERSON</td>
      <td>Thursday</td>
      <td>04/26/2007</td>
      <td>13:15:00</td>
      <td>NORTHERN</td>
      <td>NONE</td>
      <td>600 Block of EDDY ST</td>
      <td>-122.418382</td>
      <td>37.783258</td>
      <td>(37.7832583770949, -122.418382008607)</td>
      <td>7.043079e+12</td>
    </tr>
    <tr>
      <th>24</th>
      <td>171022519</td>
      <td>LARCENY/THEFT</td>
      <td>LOST PROPERTY, GRAND THEFT</td>
      <td>Monday</td>
      <td>12/18/2017</td>
      <td>18:45:00</td>
      <td>CENTRAL</td>
      <td>NONE</td>
      <td>CHESTNUT ST / POWELL ST</td>
      <td>-122.411587</td>
      <td>37.803962</td>
      <td>(37.80396234588253, -122.41158662771912)</td>
      <td>1.710225e+13</td>
    </tr>
    <tr>
      <th>25</th>
      <td>160131305</td>
      <td>LARCENY/THEFT</td>
      <td>PETTY THEFT FROM LOCKED AUTO</td>
      <td>Saturday</td>
      <td>02/13/2016</td>
      <td>16:00:00</td>
      <td>SOUTHERN</td>
      <td>NONE</td>
      <td>HARRIET ST / FOLSOM ST</td>
      <td>-122.406151</td>
      <td>37.778081</td>
      <td>(37.77808112789121, -122.40615148216322)</td>
      <td>1.601313e+13</td>
    </tr>
    <tr>
      <th>26</th>
      <td>100587291</td>
      <td>SUSPICIOUS OCC</td>
      <td>SUSPICIOUS OCCURRENCE</td>
      <td>Saturday</td>
      <td>06/26/2010</td>
      <td>03:55:00</td>
      <td>MISSION</td>
      <td>NONE</td>
      <td>3000 Block of 16TH ST</td>
      <td>-122.421083</td>
      <td>37.764911</td>
      <td>(37.764910844226, -122.421082850193)</td>
      <td>1.005873e+13</td>
    </tr>
    <tr>
      <th>27</th>
      <td>50103165</td>
      <td>LARCENY/THEFT</td>
      <td>GRAND THEFT FROM LOCKED AUTO</td>
      <td>Wednesday</td>
      <td>01/26/2005</td>
      <td>07:45:00</td>
      <td>CENTRAL</td>
      <td>NONE</td>
      <td>300 Block of CLAY ST</td>
      <td>-122.398573</td>
      <td>37.795292</td>
      <td>(37.7952923975164, -122.398573051955)</td>
      <td>5.010317e+12</td>
    </tr>
    <tr>
      <th>28</th>
      <td>80437166</td>
      <td>OTHER OFFENSES</td>
      <td>DRIVERS LICENSE, SUSPENDED OR REVOKED</td>
      <td>Saturday</td>
      <td>04/26/2008</td>
      <td>17:16:00</td>
      <td>BAYVIEW</td>
      <td>ARREST, CITED</td>
      <td>CESAR CHAVEZ ST / KANSAS ST</td>
      <td>-122.402063</td>
      <td>37.749398</td>
      <td>(37.7493979879214, -122.402063377785)</td>
      <td>8.043717e+12</td>
    </tr>
    <tr>
      <th>29</th>
      <td>110218113</td>
      <td>OTHER OFFENSES</td>
      <td>MISCELLANEOUS INVESTIGATION</td>
      <td>Wednesday</td>
      <td>03/16/2011</td>
      <td>10:30:00</td>
      <td>PARK</td>
      <td>NONE</td>
      <td>700 Block of CLAYTON ST</td>
      <td>-122.448266</td>
      <td>37.767909</td>
      <td>(37.7679091107584, -122.448266122025)</td>
      <td>1.102181e+13</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>9970</th>
      <td>90773615</td>
      <td>VEHICLE THEFT</td>
      <td>STOLEN AUTOMOBILE</td>
      <td>Wednesday</td>
      <td>07/29/2009</td>
      <td>07:00:00</td>
      <td>SOUTHERN</td>
      <td>NONE</td>
      <td>6TH ST / STEVENSON ST</td>
      <td>-122.409696</td>
      <td>37.781754</td>
      <td>(37.7817540588712, -122.409696355558)</td>
      <td>9.077362e+12</td>
    </tr>
    <tr>
      <th>9971</th>
      <td>171009573</td>
      <td>SUSPICIOUS OCC</td>
      <td>SUSPICIOUS OCCURRENCE</td>
      <td>Thursday</td>
      <td>12/14/2017</td>
      <td>09:03:00</td>
      <td>MISSION</td>
      <td>NONE</td>
      <td>DUBOCE AV / WOODWARD ST</td>
      <td>-122.420948</td>
      <td>37.769979</td>
      <td>(37.76997927943881, -122.42094803971935)</td>
      <td>1.710096e+13</td>
    </tr>
    <tr>
      <th>9972</th>
      <td>30696867</td>
      <td>LARCENY/THEFT</td>
      <td>GRAND THEFT FROM LOCKED AUTO</td>
      <td>Sunday</td>
      <td>06/08/2003</td>
      <td>02:30:00</td>
      <td>BAYVIEW</td>
      <td>NONE</td>
      <td>400 Block of BARNEVELD AV</td>
      <td>-122.403360</td>
      <td>37.741657</td>
      <td>(37.7416571720538, -122.403359514965)</td>
      <td>3.069687e+12</td>
    </tr>
    <tr>
      <th>9973</th>
      <td>66005553</td>
      <td>LARCENY/THEFT</td>
      <td>GRAND THEFT FROM LOCKED AUTO</td>
      <td>Wednesday</td>
      <td>01/25/2006</td>
      <td>22:00:00</td>
      <td>SOUTHERN</td>
      <td>NONE</td>
      <td>800 Block of FOLSOM ST</td>
      <td>-122.402246</td>
      <td>37.781089</td>
      <td>(37.7810888153345, -122.402246029097)</td>
      <td>6.600555e+12</td>
    </tr>
    <tr>
      <th>9974</th>
      <td>41309477</td>
      <td>WARRANTS</td>
      <td>WARRANT ARREST</td>
      <td>Tuesday</td>
      <td>11/16/2004</td>
      <td>13:20:00</td>
      <td>MISSION</td>
      <td>ARREST, BOOKED</td>
      <td>16TH ST / HOFF ST</td>
      <td>-122.420580</td>
      <td>37.764997</td>
      <td>(37.7649968622982, -122.420580440119)</td>
      <td>4.130948e+12</td>
    </tr>
    <tr>
      <th>9975</th>
      <td>130576957</td>
      <td>SUSPICIOUS OCC</td>
      <td>SUSPICIOUS OCCURRENCE</td>
      <td>Thursday</td>
      <td>07/11/2013</td>
      <td>23:00:00</td>
      <td>SOUTHERN</td>
      <td>NONE</td>
      <td>9TH ST / FOLSOM ST</td>
      <td>-122.411612</td>
      <td>37.773768</td>
      <td>(37.7737679567236, -122.411612378034)</td>
      <td>1.305770e+13</td>
    </tr>
    <tr>
      <th>9976</th>
      <td>61239785</td>
      <td>MISSING PERSON</td>
      <td>MISSING ADULT</td>
      <td>Monday</td>
      <td>11/20/2006</td>
      <td>05:30:00</td>
      <td>BAYVIEW</td>
      <td>LOCATED</td>
      <td>1400 Block of PHELPS ST</td>
      <td>-122.394439</td>
      <td>37.736444</td>
      <td>(37.7364438996732, -122.394438859914)</td>
      <td>6.123979e+12</td>
    </tr>
    <tr>
      <th>9977</th>
      <td>130969346</td>
      <td>ASSAULT</td>
      <td>AGGRAVATED ASSAULT OF POLICE OFFICER,BODILY FORCE</td>
      <td>Friday</td>
      <td>11/15/2013</td>
      <td>15:41:00</td>
      <td>SOUTHERN</td>
      <td>ARREST, BOOKED</td>
      <td>800 Block of BRYANT ST</td>
      <td>-122.403405</td>
      <td>37.775421</td>
      <td>(37.775420706711, -122.403404791479)</td>
      <td>1.309693e+13</td>
    </tr>
    <tr>
      <th>9978</th>
      <td>130270018</td>
      <td>LARCENY/THEFT</td>
      <td>PETTY THEFT FROM A BUILDING</td>
      <td>Thursday</td>
      <td>03/21/2013</td>
      <td>01:02:00</td>
      <td>PARK</td>
      <td>NONE</td>
      <td>4100 Block of 17TH ST</td>
      <td>-122.437906</td>
      <td>37.762376</td>
      <td>(37.7623763079838, -122.437905731311)</td>
      <td>1.302700e+13</td>
    </tr>
    <tr>
      <th>9979</th>
      <td>160168693</td>
      <td>VANDALISM</td>
      <td>MALICIOUS MISCHIEF, VANDALISM</td>
      <td>Friday</td>
      <td>02/26/2016</td>
      <td>15:25:00</td>
      <td>TARAVAL</td>
      <td>ARREST, BOOKED</td>
      <td>2300 Block of NORIEGA ST</td>
      <td>-122.488808</td>
      <td>37.753752</td>
      <td>(37.75375194458355, -122.48880789335784)</td>
      <td>1.601687e+13</td>
    </tr>
    <tr>
      <th>9980</th>
      <td>40988529</td>
      <td>LARCENY/THEFT</td>
      <td>PETTY THEFT WITH PRIOR</td>
      <td>Sunday</td>
      <td>08/29/2004</td>
      <td>17:00:00</td>
      <td>TENDERLOIN</td>
      <td>ARREST, BOOKED</td>
      <td>100 Block of OFARRELL ST</td>
      <td>-122.407244</td>
      <td>37.786565</td>
      <td>(37.7865647607685, -122.407244087032)</td>
      <td>4.098853e+12</td>
    </tr>
    <tr>
      <th>9981</th>
      <td>70576586</td>
      <td>NON-CRIMINAL</td>
      <td>LOST PROPERTY</td>
      <td>Wednesday</td>
      <td>03/07/2007</td>
      <td>08:40:00</td>
      <td>SOUTHERN</td>
      <td>NONE</td>
      <td>800 Block of BRYANT ST</td>
      <td>-122.403405</td>
      <td>37.775421</td>
      <td>(37.775420706711, -122.403404791479)</td>
      <td>7.057659e+12</td>
    </tr>
    <tr>
      <th>9982</th>
      <td>136168471</td>
      <td>LARCENY/THEFT</td>
      <td>GRAND THEFT FROM LOCKED AUTO</td>
      <td>Saturday</td>
      <td>09/14/2013</td>
      <td>13:00:00</td>
      <td>SOUTHERN</td>
      <td>NONE</td>
      <td>200 Block of INTERSTATE80 HY</td>
      <td>-122.365565</td>
      <td>37.809671</td>
      <td>(37.8096707013239, -122.365565425353)</td>
      <td>1.361685e+13</td>
    </tr>
    <tr>
      <th>9983</th>
      <td>110861637</td>
      <td>RECOVERED VEHICLE</td>
      <td>RECOVERED VEHICLE - STOLEN OUTSIDE SF</td>
      <td>Tuesday</td>
      <td>10/25/2011</td>
      <td>14:43:00</td>
      <td>BAYVIEW</td>
      <td>NONE</td>
      <td>1300 Block of INGALLS ST</td>
      <td>-122.382589</td>
      <td>37.730465</td>
      <td>(37.7304652920239, -122.382588718232)</td>
      <td>1.108616e+13</td>
    </tr>
    <tr>
      <th>9984</th>
      <td>40345587</td>
      <td>VEHICLE THEFT</td>
      <td>STOLEN AUTOMOBILE</td>
      <td>Wednesday</td>
      <td>03/24/2004</td>
      <td>21:00:00</td>
      <td>MISSION</td>
      <td>NONE</td>
      <td>24TH ST / POTRERO AV</td>
      <td>-122.406338</td>
      <td>37.753004</td>
      <td>(37.7530042877269, -122.406338412693)</td>
      <td>4.034559e+12</td>
    </tr>
    <tr>
      <th>9985</th>
      <td>140819054</td>
      <td>OTHER OFFENSES</td>
      <td>DRIVERS LICENSE, SUSPENDED OR REVOKED</td>
      <td>Sunday</td>
      <td>09/28/2014</td>
      <td>18:14:00</td>
      <td>RICHMOND</td>
      <td>ARREST, CITED</td>
      <td>FULTON ST / 30TH AV</td>
      <td>-122.489539</td>
      <td>37.772325</td>
      <td>(37.772324696627, -122.489538601712)</td>
      <td>1.408191e+13</td>
    </tr>
    <tr>
      <th>9986</th>
      <td>120709920</td>
      <td>BURGLARY</td>
      <td>BURGLARY, HOT PROWL, FORCIBLE ENTRY</td>
      <td>Wednesday</td>
      <td>09/05/2012</td>
      <td>10:06:00</td>
      <td>TARAVAL</td>
      <td>NONE</td>
      <td>100 Block of ELVERANO WY</td>
      <td>-122.461329</td>
      <td>37.730631</td>
      <td>(37.7306307008778, -122.461329068423)</td>
      <td>1.207099e+13</td>
    </tr>
    <tr>
      <th>9987</th>
      <td>90239322</td>
      <td>OTHER OFFENSES</td>
      <td>HARASSING PHONE CALLS</td>
      <td>Wednesday</td>
      <td>03/04/2009</td>
      <td>17:00:00</td>
      <td>CENTRAL</td>
      <td>NONE</td>
      <td>500 Block of GREEN ST</td>
      <td>-122.407932</td>
      <td>37.799577</td>
      <td>(37.7995771094892, -122.407931930502)</td>
      <td>9.023932e+12</td>
    </tr>
    <tr>
      <th>9988</th>
      <td>91140174</td>
      <td>ASSAULT</td>
      <td>BATTERY</td>
      <td>Thursday</td>
      <td>11/05/2009</td>
      <td>00:20:00</td>
      <td>BAYVIEW</td>
      <td>NONE</td>
      <td>17TH ST / TEXAS ST</td>
      <td>-122.395810</td>
      <td>37.765189</td>
      <td>(37.7651891001345, -122.395810281469)</td>
      <td>9.114017e+12</td>
    </tr>
    <tr>
      <th>9989</th>
      <td>80279742</td>
      <td>MISSING PERSON</td>
      <td>MISSING ADULT</td>
      <td>Friday</td>
      <td>03/07/2008</td>
      <td>23:30:00</td>
      <td>TENDERLOIN</td>
      <td>LOCATED</td>
      <td>300 Block of MASON ST</td>
      <td>-122.409661</td>
      <td>37.786439</td>
      <td>(37.7864394524764, -122.409660751795)</td>
      <td>8.027974e+12</td>
    </tr>
    <tr>
      <th>9990</th>
      <td>170927865</td>
      <td>ASSAULT</td>
      <td>BATTERY, FORMER SPOUSE OR DATING RELATIONSHIP</td>
      <td>Tuesday</td>
      <td>11/14/2017</td>
      <td>11:21:00</td>
      <td>SOUTHERN</td>
      <td>ARREST, BOOKED</td>
      <td>800 Block of BRYANT ST</td>
      <td>-122.403405</td>
      <td>37.775421</td>
      <td>(37.775420706711, -122.40340479147905)</td>
      <td>1.709279e+13</td>
    </tr>
    <tr>
      <th>9991</th>
      <td>160689633</td>
      <td>OTHER OFFENSES</td>
      <td>VIOLATION OF RESTRAINING ORDER</td>
      <td>Thursday</td>
      <td>08/25/2016</td>
      <td>09:00:00</td>
      <td>MISSION</td>
      <td>ARREST, BOOKED</td>
      <td>400 Block of ALVARADO ST</td>
      <td>-122.431019</td>
      <td>37.753944</td>
      <td>(37.753943582970585, -122.43101882896221)</td>
      <td>1.606896e+13</td>
    </tr>
    <tr>
      <th>9992</th>
      <td>80917287</td>
      <td>LARCENY/THEFT</td>
      <td>GRAND THEFT FROM LOCKED AUTO</td>
      <td>Thursday</td>
      <td>08/28/2008</td>
      <td>20:00:00</td>
      <td>NORTHERN</td>
      <td>NONE</td>
      <td>GOLDEN GATE AV / FILLMORE ST</td>
      <td>-122.431952</td>
      <td>37.779565</td>
      <td>(37.7795647498663, -122.431952436364)</td>
      <td>8.091729e+12</td>
    </tr>
    <tr>
      <th>9993</th>
      <td>40813841</td>
      <td>ASSAULT</td>
      <td>AGGRAVATED ASSAULT WITH A DEADLY WEAPON</td>
      <td>Saturday</td>
      <td>07/17/2004</td>
      <td>01:57:00</td>
      <td>MISSION</td>
      <td>ARREST, BOOKED</td>
      <td>16TH ST / HOFF ST</td>
      <td>-122.420580</td>
      <td>37.764997</td>
      <td>(37.7649968622982, -122.420580440119)</td>
      <td>4.081384e+12</td>
    </tr>
    <tr>
      <th>9994</th>
      <td>146231278</td>
      <td>LARCENY/THEFT</td>
      <td>GRAND THEFT FROM LOCKED AUTO</td>
      <td>Wednesday</td>
      <td>11/05/2014</td>
      <td>09:45:00</td>
      <td>CENTRAL</td>
      <td>NONE</td>
      <td>NORTHPOINT ST / LARKIN ST</td>
      <td>-122.422009</td>
      <td>37.805496</td>
      <td>(37.8054960276478, -122.422008950077)</td>
      <td>1.462313e+13</td>
    </tr>
    <tr>
      <th>9995</th>
      <td>140224390</td>
      <td>OTHER OFFENSES</td>
      <td>DRIVERS LICENSE, SUSPENDED OR REVOKED</td>
      <td>Sunday</td>
      <td>03/16/2014</td>
      <td>18:30:00</td>
      <td>INGLESIDE</td>
      <td>ARREST, CITED</td>
      <td>PERSIA AV / MADRID ST</td>
      <td>-122.432805</td>
      <td>37.721618</td>
      <td>(37.7216179113708, -122.432804728335)</td>
      <td>1.402244e+13</td>
    </tr>
    <tr>
      <th>9996</th>
      <td>140531101</td>
      <td>VEHICLE THEFT</td>
      <td>STOLEN AUTOMOBILE</td>
      <td>Thursday</td>
      <td>06/26/2014</td>
      <td>18:00:00</td>
      <td>SOUTHERN</td>
      <td>NONE</td>
      <td>0 Block of GOUGH ST</td>
      <td>-122.421206</td>
      <td>37.772531</td>
      <td>(37.7725305162673, -122.421205551035)</td>
      <td>1.405311e+13</td>
    </tr>
    <tr>
      <th>9997</th>
      <td>70416857</td>
      <td>BURGLARY</td>
      <td>BURGLARY OF RESIDENCE, UNLAWFUL ENTRY</td>
      <td>Monday</td>
      <td>04/23/2007</td>
      <td>09:15:00</td>
      <td>TARAVAL</td>
      <td>ARREST, BOOKED</td>
      <td>1700 Block of 44TH AV</td>
      <td>-122.503257</td>
      <td>37.753978</td>
      <td>(37.7539775965639, -122.503257080708)</td>
      <td>7.041686e+12</td>
    </tr>
    <tr>
      <th>9998</th>
      <td>130481259</td>
      <td>DRUG/NARCOTIC</td>
      <td>SALE OF MARIJUANA</td>
      <td>Tuesday</td>
      <td>06/11/2013</td>
      <td>16:07:00</td>
      <td>SOUTHERN</td>
      <td>ARREST, BOOKED</td>
      <td>900 Block of MARKET ST</td>
      <td>-122.408595</td>
      <td>37.783707</td>
      <td>(37.7837069301545, -122.408595110869)</td>
      <td>1.304813e+13</td>
    </tr>
    <tr>
      <th>9999</th>
      <td>146101245</td>
      <td>LARCENY/THEFT</td>
      <td>GRAND THEFT FROM UNLOCKED AUTO</td>
      <td>Sunday</td>
      <td>05/18/2014</td>
      <td>00:45:00</td>
      <td>SOUTHERN</td>
      <td>NONE</td>
      <td>HARRISON ST / 5TH ST</td>
      <td>-122.401846</td>
      <td>37.779032</td>
      <td>(37.7790324136251, -122.401846367522)</td>
      <td>1.461012e+13</td>
    </tr>
  </tbody>
</table>
<p>10000 rows × 13 columns</p>
</div>
</div>





{:.input_area}
```python
#ts = Table(data.labels)
import pandas as pd
from sodapy import Socrata

# Unauthenticated client only works with public data sets. Note 'None'
# in place of application token, and no username or password:
client = Socrata("data.sfgov.org", None)

# Example authenticated client (needed for non-public datasets):
# client = Socrata(data.sfgov.org,
#                  MyAppToken,
#                  userame="user@example.com",
#                  password="AFakePassword")

# First 2000 results, returned as JSON from API / converted to Python list of
# dictionaries by sodapy.
results = client.get("tmnf-yvry", limit=2000)

# Convert to pandas DataFrame
results_df = pd.DataFrame.from_records(results)
```


{:.output .output_traceback_line}
```

    ---------------------------------------------------------------------------

    ModuleNotFoundError                       Traceback (most recent call last)

    <ipython-input-17-c5d4879f0181> in <module>()
          1 #ts = Table(data.labels)
          2 import pandas as pd
    ----> 3 from sodapy import Socrata
          4 
          5 # Unauthenticated client only works with public data sets. Note 'None'


    ModuleNotFoundError: No module named 'sodapy'


```



{:.input_area}
```python
import pandas as pd
df = pd.DataFrame(recs)
df.head()
```





<div markdown="0" class="output output_html">
<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>code</td>
    </tr>
    <tr>
      <th>1</th>
      <td>error</td>
    </tr>
    <tr>
      <th>2</th>
      <td>message</td>
    </tr>
    <tr>
      <th>3</th>
      <td>data</td>
    </tr>
    <tr>
      <th>4</th>
      <td>code</td>
    </tr>
  </tbody>
</table>
</div>
</div>





{:.input_area}
```python
data = Table.from_df(df.drop('location', axis=1))
data
```


{:.output .output_traceback_line}
```

    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-10-cf486b52f37a> in <module>()
          1 # data = Table.from_df(df.drop('location', axis=1))
    ----> 2 data
    

    NameError: name 'data' is not defined


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


{:.output .output_traceback_line}
```

    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-9-8d418cf325f3> in <module>()
    ----> 1 data['y'] = data['y'].astype('float')
          2 data['x'] = data['x'].astype('float')


    NameError: name 'data' is not defined


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

