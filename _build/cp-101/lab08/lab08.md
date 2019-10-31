---
interact_link: content/cp-101/lab08/lab08.ipynb
kernel_name: python3
has_widgets: false
title: 'Lab 8'
prev_page:
  url: /cp-101/lab07/lab07.html
  title: 'Lab 7'
next_page:
  url: /cp-101/lab09/lab09.html
  title: 'Lab 9'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---
# Web Scraping
---
In today's lab, we are going to download data from the internet using an API. API stands for application programming interface. Companies often create APIs as a way to allow users to more directly interact with their servers to retrieve data. Today, we are going to be using Twitter's API to download tweets to get some experience with larger datasets.



{:.input_area}
```python
# Run this cell to set up your notebook
import csv
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import zipfile
import warnings

# These are the utility functions in the twitter_utils.py file
from twitter_utils import *

# Ensure that Pandas shows at least 280 characters in columns, so we can see full tweets
pd.set_option('max_colwidth', 280)

%matplotlib inline
import re
import json
```


## Setup
---
For this lab, we will be importing utility functions to interact with Twitter's API. Underneath the hood, these utility functions use the `tweepy` package, which is the how you can interface with Twitter's API using `python`. First, we need to install `tweepy` so that our utility functions will be able to use use it. If you have time at the end of this lab, you can look in the `twitter_utils.py` file in this folder and try to understand how the utility functions work.

Twitter requires you to have authentication keys to access their API.  To get your keys, you'll have to sign up for a Twitter developer account. Note that **anyone who has your authentication keys can post as you**. In order to protect your keys, you will be storing them in a separate file, which we have called `keys.json`, and reading them into this notebook from that file. Also note that **Twitter limits developers to a certain rate of data requests**. This means that if you make too many API calls in a short period of time, Twitter may block you from retrieving data for a certain period of time. Avoid rerunning cells that retrieve new tweets.

Follow the instructions below to get your Twitter API keys.  **Read the instructions completely before starting.**

1. [Create a Twitter account](https://twitter.com).  You can use an existing account if you have one; if you prefer to not do this assignment under your regular account, feel free to create a throw-away account.
2. Under account settings, add your phone number to the account.
3. [Create a Twitter developer account](https://dev.twitter.com/resources/signup) by clicking the 'Apply' button on the top right of the page. Attach it to your Twitter account. You'll have to fill out a form describing what you want to do with the developer account. Explain that you are doing this for a class at UC Berkeley and that you don't know exactly what you're building yet and just need the account to get started. These applications are approved by some sort of AI system, so it doesn't matter exactly what you write.
4. Once you're logged into your developer account, [create an application for this assignment](https://apps.twitter.com/app/new).  You can call it whatever you want, and you can write any URL when it asks for a web site.  You don't need to provide a callback URL.
5. On the page for that application, find your Consumer Key and Consumer Secret.
6. On the same page, create an Access Token.  Record the resulting Access Token and Access Token Secret.
7. Edit the file `keys.json` in the same folder as this file and replace the placeholders with your keys.

Now you should be all ready to go! Let's test that you have correctly set up your developer account and the `keys.json` folder. The following cell loads your keys into this notebook, then validates them with the Twitter API. It should display your Twitter username without any warnings.



{:.input_area}
```python
import json
key_file = "keys.json" # Add your keys to keys.json before running this cell

# Loading your keys from keys.json
with open(key_file) as f:
    keys = json.load(f)
# if you print or view the contents of keys be sure to delete the cell!

# Validate keys.
# If your notebook does not print out "The keys are valid. Your username is: <your username>"
# you may have copied and pasted your keys incorrectly.
validate_authentication(keys)
```


If you are getting any errors in this cell, ask a TA for help. If you do not have valid keys, you will not be able to use the API.

## Downloading Tweets
---
Now we should be ready to download some tweets! In the following cell, we use one of the utility functions to download recent tweets with the hashtag "#gentrification". This cell can take a few minutes to finish running.



{:.input_area}
```python
# Note that you do not write the actual hashtag symbol
gentrification = download_recent_tweets_by_hashtag(hashtag = "gentrification",
                                                   keys = keys,
                                                   count = 100)
```


If you are running into errors downloading these tweets, uncomment and run the following cell to load in tweets that we scraped earlier.



{:.input_area}
```python
# gentrification = load_tweets('gentrification.json')
```


Similarly, if you download any datasets during this lab that you would like to save for later, you can use the `save_tweets()` function, which takes as its arguments a list of dictionaries and a name for the new file you are writing.

We now have `gentrification` assigned to a list with each element corresponding to a tweet. Let's examine one of these elements to get a better understanding of our data.



{:.input_area}
```python
# This accesses the first (zero index) element of the list
gentrification[0]
```


This is an example of another `python` data structure called a *dictionary*. Dictionaries store *values* by associating them with a *key* rather than by an integer index. You can access the values stored in a dictionary using bracket notation just like a list. For example:



{:.input_area}
```python
# In this dictionary, the keys are strings, and the values are all numbers
d = {'a': 1,
    'b': 2,
    'c': 3}

d['a']
```


## Data Cleaning
---
The dictionary we were looking at above is a little bit hard to interpret because there dictionaries nested inside of some our keys. We can look only at the first level of keys in our dictionary by using the `.keys()` method.



{:.input_area}
```python
gentrification[0].keys()
# You can also use .values() to access all of the values
```


Unfortunately, Twitter by default does not attach geographic data to the metadata of each tweet. To get around this, we can use the location associated to the account of each poster. First, we want to extract only the parts of the data that are relevant to what we are looking for. To do this, we first need to turn our list of dictionaries into a `pandas DataFrame`. Fortunately, there is a function that can do this easily for us.



{:.input_area}
```python
gentrification_df = pd.DataFrame(gentrification)
gentrification_df.head()
```


Next, we want to extract out only the columns that are relevant to us. Discarding columns that do not help us answer our question can be helpful because it prevents the computer from having to do unnecessary computations. However, if we want to be able to connect any conclusions we make after we get rid of columns, it is helpful to keep an identifying column in your `DataFrame` even if you are not performing analyses on it.



{:.input_area}
```python
users = gentrification_df[['id', 'user']]
```


Let's take a closer look at an element of the `user` column.



{:.input_area}
```python
users.loc[0, 'user']
```


In each row, the `user` column contains another dictionary with information about the user who posted the tweet. We can access the user's location using the `location` key.

The strategy that we are going to use to extract the locations from each user will be to iterate through the rows of `users`; at each row we will add the tweet id and the user location to a new dictionary. This dictionary will then be added to a list. Once we have iterated through all of the rows of `users`, we will convert our final list of dictionaries into a `DataFrame`.



{:.input_area}
```python
# Create an empty list.
locations_list = list()

for i in range(len(users)):
    # Create an empty dictionary.
    new_entry = {}
    # Copy the tweet id into the new dictionary.
    new_entry['id'] = users.loc[i, 'id']
    # Create a new key ('location') and assign it to the location of the user who
    # wrote that tweet.
    new_entry['location'] = users.loc[i, 'user']['location']
    # Append the dictionary as another element of our list.
    locations_list.append(new_entry)
    
# Transform our list into a DataFrame. As before, each element of the list becomes
# a row in the DataFrame, and each key becomes a column.
all_locations = pd.DataFrame(locations_list)

# Display the first 10 tweets.
all_locations.head(10)
```


Clearly this isn't a foolproof method, since the location associated with an account may have little bearing on the actual location from which a tweet was posted. Also, not all users have a specific location connected to their account. Depending on the data you have pulled from Twitter, you may also notice that some of the "locations" are not actually real places. We can do a bit of data cleaning to filter out the rows that contain true locations. First, let's get rid of the rows that do not contain any text at all in the `location` column.



{:.input_area}
```python
# Create an empty DataFrame with the columns 'location' and 'id'
no_empties = pd.DataFrame(columns = ['id', 'location'])
for i in range(len(all_locations)):
    # This filters out tweets whose location column is an empty string.
    if all_locations.loc[i, "location"] != '':
        no_empties = no_empties.append(all_locations.loc[i,:])
no_empties.head(10)
```


This looks pretty good! We would still like to filter through our locations for places that actually exist. Let's use the `.groupby()` method to take a look at what locations we have in our data.

The `.groupby()` method takes in a table, a column, and optionally, an aggregate function (the default is count() which counts how many rows have the same value for the column we are grouping by. Other options include sum() and max() or min()). Groupby goes through each row, looks at the column that has been given to it of the current row, and groups each row based on if they have the same value at given column. After it has a list of rows for each distinct column value, it applies the aggregate function for each list, and returns a table of each distinct column value with the aggregate function applied to the rows that corresponded with the column.



{:.input_area}
```python
no_empties.groupby('location').count()
```


If you scroll through this list, you will likely see a whole litany of "locations" that do not resemble locations since the user is allowed to write whatever they like as their location. We do not have time to day to sort through all of these right now, so we are goign to move on to a few other techniques that we can use to analyze these kinds of data.

## Scraping Tweets by Location
---
Since many of the tweets we scraped earlier do not have useful locations, we may want to filter by location when we ask the API for tweets. We can use the same function as before, using the optional `location` argument. The format of the location argument is `"latitude,longitude,radius"`. The following code searches for tweets hashtagged "gentrification" within a 5 km radius of the Temescal Oakland area.



{:.input_area}
```python
gentrification_oak = download_recent_tweets_by_hashtag(hashtag = "gentrification",
                                                       keys = keys,
                                                       location = "37.829314,-122.264433,5km",
                                                       count = 100)
```


If you are running into errors downloading these tweets, uncomment and run the following cell to load in tweets that we scraped earlier.



{:.input_area}
```python
# gentrification_oak = load_tweets('gentrification_oak.json')
```


**Your turn:** Let's use the procedure we went through earlier to find the most common user location in the `gentrification_oak` tweets. We've provided some starter code, but you need to fill in wherever you see a `...`!



{:.input_area}
```python
users_oak = pd.DataFrame(gentrification_oak)
users_oak = ... # select columns of interest

locations_list_oak = list()
for i in range(len(users_oak)):
    new_entry = {}
    new_entry['id'] = users_oak.loc[i, 'id']
    new_entry['location'] = users_oak.loc[i, 'user']['location']
    locations_list_oak.append(...) # we want to add the new entry to our list
all_locations_oak = ... # turn the list into a DataFrame

no_empties_oak = pd.DataFrame(columns = ['id', 'location'])
for i in range(len(all_locations_oak)):
    if all_locations_oak.loc[i, "location"] != '':
        no_empties_oak = no_empties_oak.append(all_locations_oak.loc[i,:])
        
grouped_locations = ...

# This finds the number of repeats of the most common location.
max_number_of_tweets = grouped_locations['id'].max()

most_common_location = grouped_locations[grouped_locations['id'] == max_number_of_tweets]

# most_common_location is a DataFrame with one item. This access all of the indices in the
# DataFrame, then takes the first (and only) one.
most_common_location.index[0]
```


## Temporal Data
---
Another facet of the tweets that you may want to analyze is the time at which they were posted. Currently, the only way we have information about the time the tweets were posted is in the `'created_at'` column, which is a string. As you may remember from the Introductory lab, `python` compares strings by assigning values to the letters themselves based on their position in the alphabet. We want to convert these strings to `datetime` objects, which will tell `python` at what time tweets were posted.



{:.input_area}
```python
post_time = pd.DataFrame(gentrification_oak)[['id', 'created_at']]
post_time['time'] = pd.to_datetime(post_time['created_at'])
post_time['time'].head()
```


Now that each string has been converted into a `datetime` object, we can extract the day, hour, minute, etc. of each time point like so



{:.input_area}
```python
post_time.loc[0, 'time'].day
```




{:.input_area}
```python
post_time.loc[0, 'time'].hour
```




{:.input_area}
```python
post_time.loc[0, 'time'].minute
```


Notice that we are not adding parentheses at the end of each line. That is because the `.day`, `.hour`, and `.minute` are not *functions* we are calling, but rather *attributes* of the particular `datetime` object. If we want to look at the time of day that people tend to tweet about #gentrification, we can extract these attributes.



{:.input_area}
```python
post_time['hour'] = [post_time.loc[i, 'time'].hour + post_time.loc[i, 'time'].minute/60 +
                     post_time.loc[i, 'time'].second/3600 for i in range(len(post_time))]
post_time['hour'].hist()
plt.xlabel("Hour (UTC)")
plt.ylabel("Number of Tweets");
```


**Question:** What observations or trends do you notice about this graph?

**Question:** What could be improved about this graph or the process we used to obtain the data that generated it?

## Sentiment Analysis
---
We can use the words the tweets to measure the sentiment, or the positive/negative feeling generated by the tweet. To do so we will be using the [VADER (Valence Aware Dictionary and sEntiment Reasoner)](https://github.com/cjhutto/vaderSentiment), which is a rule-based sentiment analysis tool specifically designed for social media. It even includes emojis! Run the following cell to load in the lexicon.



{:.input_area}
```python
vader = load_vader()
vader.iloc[500:510, :]
```


The more positive the polarity of a word, the more positive feeling the word evokes in the reader. All of the words in `vader` are all lowercase, while many of our tweets are not. We need to modify the text in the tweets so that the words in our tweets will match up with the words stored in `vader`. Additionally, we need to remove punctuation since that will cause the words to not match up as well. We will put these modified tweets into another column in our `DataFrame` so that we can still have access to them later.



{:.input_area}
```python
# Select our columns of interest
tweets_and_retweets = pd.DataFrame(gentrification_oak)[['id', 'text', 'retweet_count']]

# Set the index of the DataFrame to the tweet ID. This step is necessary
# in order to use our utility functions.
tweets_and_retweets.set_index('id', inplace = True)

# Remove punctuation and lowercase tweets
tweets_and_retweets['cleaned'] = clean_tweets(tweets_and_retweets['text'])

tweets_and_retweets.head()
```


Next, we want to merge our sentiment lexicon with our cleaned tweets. 



{:.input_area}
```python
tweets_and_retweets['polarity'] = compose_polarity(tweets_and_retweets, vader)
tweets_and_retweets.head()
```


Next, we want to see if more polarizing tweets are retweeted more often. To do this, we can plot the `polarity` and `retweet_count` columns against each other.



{:.input_area}
```python
tweets_and_retweets.plot('polarity', 'retweet_count', kind='scatter');
```


**Question:** What conclusions can you draw about polarity and retweets from this graph? How does this compare with your assumptions?

## Your turn!
---
If time allows, try these exercises on your own or as a class!

**Exercise 1:** Using the `gentrification_oak` tweets, make a histogram of the time of day the tweets were posted. Note that if you would like the x-axis of the plot to reflect the correct time of day, you will have to convert the time from UTC to PDT.



{:.input_area}
```python
# YOUR CODE HERE
```


**Exercise 2:** Try scraping tweets from multiple locations and the same hashtag. Make a histogram for each location and see if there are any differences in the distribution of polarity of the tweets. Feel free to use multiple cells to avoid querying the API repeatedly.



{:.input_area}
```python
# YOUR CODE HERE
```


### Authors: Monica Wilkinson and Vera Wang
