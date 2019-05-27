---
interact_link: content/rhetoric/01-intro/01-intro.ipynb
kernel_name: python3
title: 'Introduction'
prev_page:
  url: /rhetoric/rhetoric-intro
  title: 'Rhetoric'
next_page:
  url: /rhetoric/02-Moral-Foundations-Analysis/02-Moral-Foundations-Analysis
  title: 'Moral Foundations Analysis'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---

# XRHETOR-R1A Data Science Module

## 01 - Intro to Data Science in Rhetoric

## Professor Amy Tick

Data Science is a fast-growing discipline with applications in many fields. Over the course of the next week, these modules will explore the use of Data Science in Rhetoric. Module 01 introduces the Python programming language and the Pandas DataFrame table structure and shows how to apply coding skills exploratory analysis for text data. Module 02 walks through the data science process start to finish to test Moral Foundations Theory. Finally, Module 03 examines data science as a rhetorical tool: how human biases, conscious or unconscious, affect how data is processed and perceived. 

Estimated Time: 50 minutes

## __Topics Covered__

### Data Science Intro
- The field of Data Science <br>
- Environment (Jupyter Notebook/Data hub)<br>
- Basic Python
- Introduction to Pandas DataFrames

### Data
- Election 2016 <br> http://www.presidency.ucsb.edu/2016_election.php <br>

### Text processing
- String manipulation
- Word counts

### What you need to know
- data type
- expression
- names
- call expression
- attribute operator
- lists
- dict
- importing library
- table
- functions

**Dependencies: datascience, nltk, pandas

## Before we begin
Please help us better establish the audience that we are reaching by filling out this survey:
https://docs.google.com/forms/d/1f7EekVoQYHaFeXpzKUul_ZrxzvXz_Iso5aDOMXNl8ic/edit?usp=sharing

## What is Datascience?
### Data science is an interdisciplinary field that seeks to extract knowledge or insights from various forms of data.

<img src="http://www.kiwidatascience.com/wp/wp-content/uploads/2016/01/data_scientist.png" style="width: 550px; height: 500px;\" />
Statistics is a central component of data science because statistics studies how to make robust conclusions with incomplete information. Computing is a central component because programming allows us to apply analysis techniques to the large and diverse data sets that arise in real-world applications. Domain knowlege is the most important compoent among above. Domain expertise is perhaps most relevant in the interpretation of insights. Without knowlege in the domain of the subject, we can't decide what to analyze.

## The Jupyter Notebook

Note that this page is divided into what are called "cells". For example, the following cell is a "code cell" where you will write your code. You'll see a In [ ]: next to each cell for code, which is a counter for the cells you have run. You can navigate cells by clicking on them or by using the up and down arrows. Cells will be highlighted as you navigate them.



{:.input_area}
```python
# this is a code cell
```


## Python

### Data Types

Text analysis uses two basic types of data: numbers and text. 

In Jupyter notebooks, Python numbers are shown in green. 

Python text is referred to as a **string** and is written inside of single or double quotation marks. Jupyter shows it in red.



{:.input_area}
```python
# Numbers in Python
3
6.0
1837720.8787623
```





{:.output .output_data_text}
```
1837720.8787623
```





{:.input_area}
```python
# Python text, aka strings
"a"
"word"
"The quick brown fox jumped over the lazy dog"
```





{:.output .output_data_text}
```
'The quick brown fox jumped over the lazy dog'
```



### Expressions
Programs are made up of expressions, which describe to the computer how to combine pieces of data. 

Running a code cell will output the result of the expression below the cell. Code cells are run by navigating to the cell and pressing `Shift` + `Enter`.



{:.input_area}
```python
# number expression
3 * 4
```





{:.output .output_data_text}
```
12
```





{:.input_area}
```python
24 * 7
```





{:.output .output_data_text}
```
168
```



### Names (Identifiers)
Names are given to values in Python using an assignment statement. In an assignment, a name is followed by =, which is followed by any expression. The value of the expression to the right of = is assigned to the name.



{:.input_area}
```python
#if you want to save it for later use
hours_per_week = 24 * 7
```




{:.input_area}
```python
hours_per_week * 60
```





{:.output .output_data_text}
```
10080
```





{:.input_area}
```python
seconds_per_year = 60 * 60 * 24 * 365
```




{:.input_area}
```python
seconds_per_year
```





{:.output .output_data_text}
```
31536000
```





{:.input_area}
```python
seconds_per_hour = 60 * 60
hours_per_year = 24 * 365
seconds_per_year = seconds_per_hour * hours_per_year
seconds_per_year
```





{:.output .output_data_text}
```
31536000
```



### Call Expressions

The most important kind of compound expression is a call expression, which applies a function to some arguments. Recall from algebra that the mathematical notion of a function is a mapping from some input arguments to an output value. The way in which Python expresses function application is the same as in conventional mathematics.

For instance, the abs function maps its single inputs to a single output, which is the absolute value of the inputs. 



{:.input_area}
```python
abs(-5)
```





{:.output .output_data_text}
```
5
```



For instance, the max function maps its inputs to a single output, which is the largest of the inputs.



{:.input_area}
```python
max(3, 4)
```





{:.output .output_data_text}
```
4
```





{:.input_area}
```python
y = max(3, 4)
```




{:.input_area}
```python
y
```





{:.output .output_data_text}
```
4
```



### Attribute Operator
A few functions are available by default, such as abs and max, but most functions that are built into the Python language are stored in a collection of functions called a module. An import statement is used to provide access to a module, such as math or operator. Operators and call expressions can be used together in an expression.

Put another way, specific types of data have specific functions that can be used with **dot notation**. The order of the syntax goes `data` then a '.' then the function. 

For example, the `upper()` function can be called on a string to make all of its characters uppercase.



{:.input_area}
```python
message = "python is fun"
```




{:.input_area}
```python
message.upper()
```





{:.output .output_data_text}
```
'PYTHON IS FUN'
```



### Lists

Python has a great built-in list type named "list". Items in a list are written within square brackets [ ] and separated by commas. Lists work similarly to strings -- use square brackets [ ] to access data, with the first element at index 0.



{:.input_area}
```python
colors = ['red', 'blue', 'green']
```




{:.input_area}
```python
colors[0]    ## red
```





{:.output .output_data_text}
```
'red'
```





{:.input_area}
```python
colors[2]    ## green
```





{:.output .output_data_text}
```
'green'
```





{:.input_area}
```python
len(colors)  ## 3
```





{:.output .output_data_text}
```
3
```



### Dict (Python dictionary)

Python also has a **dictionary** structure called a "dict". The contents of a dict can be written as a series of key:value pairs within braces { }, e.g. dict = {key1:value1, key2:value2, ... }. The "empty dict" is just an empty pair of curly braces {}.



{:.input_area}
```python
## Can build up a dict by starting with the the empty dict {}
## and storing key/value pairs into the dict like this:
## dict[key] = value-for-that-key
dict = {}
dict['a'] = 'alpha'
dict['g'] = 'gamma'
dict['o'] = 'omega'
```




{:.input_area}
```python
dict
```





{:.output .output_data_text}
```
{'a': 'alpha', 'g': 'gamma', 'o': 'omega'}
```





{:.input_area}
```python
dict['a']     ## Simple lookup, returns 'alpha'
```





{:.output .output_data_text}
```
'alpha'
```





{:.input_area}
```python
dict['a'] = 6       ## Put new key/value into dict
```




{:.input_area}
```python
'a' in dict         ## True
```





{:.output .output_data_text}
```
True
```



### Errors

The Python language has a very specific syntax. If code is not written in that syntax, running a cell will result in an **error** and show an error message.

Error messages can be confusing, but they can also give information about what is wrong.



{:.input_area}
```python
# Un-comment the next line, then run the cell to create an error
# dict['b']
```


### Importing Library Functions

Python defines a very large number of functions, including the operator functions mentioned in the preceding section, but does not make all of their names available by default. Instead, it organizes the functions and other quantities that it knows about into modules, which together comprise the Python Library. To use these elements, one imports them.
These libraries below are what we are using in this demo.



{:.input_area}
```python
import pandas as pd
import json
from collections import Counter
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize
from nltk.corpus import wordnet as wn
from nltk.stem.snowball import SnowballStemmer
```


## Data Source
http://www.presidency.ucsb.edu/2016_election.php 



{:.input_area}
```python
# All the csv files are prepared.
# We are not going to cover web scraping but you can see the code later if you have interest.

# Loading csv data to jupyter notebook and save it as table.

clinton_press = pd.read_csv("../mft_data/csv/Clinton_p.csv")
```


## Using DataFrame in pandas


A DataFrame is a 2-dimensional labeled data structure with columns of potentially different types. You can think of it like a spreadsheet or table.

Each row represents one **entry**: in this case, a speech, statement, or press release. Each column column describes an **aspect** of entries, like the title or date of the speech.

The `head()` function shows us the first five rows of the table.



{:.input_area}
```python
clinton_press.head()
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
      <th>Candidate</th>
      <th>Party</th>
      <th>Type</th>
      <th>Date</th>
      <th>Title</th>
      <th>Speech</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Hillary Clinton</td>
      <td>D</td>
      <td>p</td>
      <td>January 20, 2007</td>
      <td>Press Release - Clinton Candidacy Garners Huge...</td>
      <td>Campaign web site signs up 100 new members per...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Hillary Clinton</td>
      <td>D</td>
      <td>p</td>
      <td>January 20, 2007</td>
      <td>FYI: New Washington Post-ABC Poll Shows Senato...</td>
      <td>The new Washington Post-ABC poll out this afte...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Hillary Clinton</td>
      <td>D</td>
      <td>p</td>
      <td>January 21, 2007</td>
      <td>Press Release - 24 Hours Later, the Reviews Ar...</td>
      <td>Top pundits on Hillary's announcement: 'brilli...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Hillary Clinton</td>
      <td>D</td>
      <td>p</td>
      <td>January 22, 2007</td>
      <td>Press Release - Conversation Begins Tonight</td>
      <td>Senator Clinton's first video webcast is live ...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Hillary Clinton</td>
      <td>D</td>
      <td>p</td>
      <td>January 25, 2007</td>
      <td>Press Release - Clinton Hires Former Harkin Ch...</td>
      <td>Fourth-generation Iowan is veteran of numerous...</td>
    </tr>
  </tbody>
</table>
</div>
</div>



While `shape` shows the number of rows and columns.



{:.input_area}
```python
# A csv file is either campaign speeches, statements or press releases of a candidate.
# This is an example of candiate "Hillary" and her press releases
# A single press release is saved in "Speech" column
# How many press releases do we have?
clinton_press.shape
```





{:.output .output_data_text}
```
(1925, 6)
```



To select a single column, put the column name in square brackets next to the DataFrame (similar to looking up an entry in a Python dictionary).



{:.input_area}
```python
# Selecting a single column
title_col = clinton_press['Title']
title_col.head()
```





{:.output .output_data_text}
```
0    Press Release - Clinton Candidacy Garners Huge...
1    FYI: New Washington Post-ABC Poll Shows Senato...
2    Press Release - 24 Hours Later, the Reviews Ar...
3          Press Release - Conversation Begins Tonight
4    Press Release - Clinton Hires Former Harkin Ch...
Name: Title, dtype: object
```



Items in a column can be accessed like items in a Python list using square brackets.



{:.input_area}
```python
title_col[0]
```





{:.output .output_data_text}
```
'Press Release - Clinton Candidacy Garners Huge Online Response'
```



Select a row using `.loc[]` with the number of the row inside the brackets. 

A range of rows can be selected by giving two numbers separated by a colon. The first number is the first row returned, and the last number is the last row returned.



{:.input_area}
```python
# Locate the 1st row
clinton_press.loc[1]
```





{:.output .output_data_text}
```
Candidate                                     Hillary Clinton 
Party                                                        D
Type                                                         p
Date                                          January 20, 2007
Title        FYI: New Washington Post-ABC Poll Shows Senato...
Speech       The new Washington Post-ABC poll out this afte...
Name: 1, dtype: object
```





{:.input_area}
```python
# Locate the 50th-55th rows
clinton_press.loc[50:55]
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
      <th>Candidate</th>
      <th>Party</th>
      <th>Type</th>
      <th>Date</th>
      <th>Title</th>
      <th>Speech</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>50</th>
      <td>Hillary Clinton</td>
      <td>D</td>
      <td>p</td>
      <td>April 1, 2007</td>
      <td>Press Release - Clinton Reports $36 Million in...</td>
      <td>Total includes $26 million raised since Jan 20...</td>
    </tr>
    <tr>
      <th>51</th>
      <td>Hillary Clinton</td>
      <td>D</td>
      <td>p</td>
      <td>April 2, 2007</td>
      <td>Gov. Corzine, NJ Officials Endorse Clinton</td>
      <td>The Clinton Campaign today announced the endor...</td>
    </tr>
    <tr>
      <th>52</th>
      <td>Hillary Clinton</td>
      <td>D</td>
      <td>p</td>
      <td>April 3, 2007</td>
      <td>Press Release - Clinton Launches Petition Call...</td>
      <td>Bush Renews Veto Threat Today, Defying Congres...</td>
    </tr>
    <tr>
      <th>53</th>
      <td>Hillary Clinton</td>
      <td>D</td>
      <td>p</td>
      <td>April 5, 2007</td>
      <td>Press Release - Nine More NH State Representat...</td>
      <td>NH House Support Continues to Grow; Now Totals...</td>
    </tr>
    <tr>
      <th>54</th>
      <td>Hillary Clinton</td>
      <td>D</td>
      <td>p</td>
      <td>April 6, 2007</td>
      <td>Clinton to Participate in South Carolina Debate</td>
      <td>The Clinton campaign announced today that Hill...</td>
    </tr>
    <tr>
      <th>55</th>
      <td>Hillary Clinton</td>
      <td>D</td>
      <td>p</td>
      <td>April 10, 2007</td>
      <td>Press Release - From the Senate: Senator Clint...</td>
      <td>Visit to three Upstate New York VA &amp; Military ...</td>
    </tr>
  </tbody>
</table>
</div>
</div>



These filtering tools help us in text analysis. In the next section, we'll analyze the first speech in the DataFrame. Run the next cell to select the speech and save it to a variable.



{:.input_area}
```python
a_speech = clinton_press["Speech"][0]
a_speech
```





{:.output .output_data_text}
```
'Campaign web site signs up 100 new members per minute, racks up 10,000 messages of support within 6 hours of announcement  Clinton candidacy hailed online as "profoundly moving"; "top tier"; "exciting"; "remarkable"; "smart"; and "news of a generation" Demonstrating the groundswell of enthusiasm generated by her historic candidacy, Senator Hillary Rodham Clinton\'s announcement for President lit up the internet today, garnering rave reviews in the blogosphere, and thousands of supporters flocking to her web site each hour. Within just six hours of the announcement going live on her campaign web site, Senator Clinton\'s candidacy attracted thousands of messages of support, and widespread accolades online. Overwhelming Response Within Hours of Going Live:  SIGN UPS = 100 per minute MESSAGES OF SUPPORT = 10,000 VIDEO WEBCAST SIGN-UPS = 7,700 BLOG CONTEST SUBMISSIONS = 2,200  Bloggers Give Clinton Announcement Rave Reviews: MYDD (Jerome Armstrong) - "And as blogger savvy as John Edwards was in outreach, Clinton internet team had the emails of bloggers to notify them separate from the press (no such outreach from the Obama camp). The website has the clean, Kerry-2004 look about it. A smart "write our first post" call to action on the website. The announcement of "an unprecedented series of video webcasts beginning Monday, January 22nd at 7pm EST for three nights" creates a quick narrative of interaction and response around Bush\'s SOTU address." DAILY KOS DIARY (nyceve) - "I\'m an open and honest person, and I\'m profoundly moved by her announcement. What was unimaginable just a few decades ago, is now something we can almost touch." THE CARPETBAGGER REPORT - "Clinton enters the race, without a doubt, at the top of the top tier. I\'ve heard all the various concerns about her candidacy, but I don\'t have any doubt that she has what it takes to win. Indeed, Clinton brings an enormous amount of talent, experience, and intelligence to the table." TAYLOR MARSH - "Sitting in a living room setting, Senator Hillary Clinton made one simple statement that changed the landscape of the \'08 presidential tournament to come. (To add, I got an email about this event this morning just after 6:00 a.m.) Because when the first woman to run for president, with an actual chance of winning, puts her name and reputation on the line, it becomes news of the day, week, even a generation." TALK LEFT - It is exciting to have a serious female candidate for President. OUTSIDE THE BELTWAY - After nearly eight years of speculation, Hillary Clinton has announced her candidacy for president.... she has done a remarkable job these past several years getting out of her husband\'s shadow, positioning herself as more moderate than previously thought, and garnering bipartisan praise for collegiality and hard work in the Senate. DAILY KOS DIARY (Yellow Dog Blue) - "How has she survived and thrived? Not by heavying up her armor. Not by engaging and overwhelming her opponents. Not even by appealing for public sympathy. Instead Hillary has just gone her business being a Senator, building personal relationships and support, getting and using power. And I really admire that." SEEING THE FOREST (Dave Johnson) - "People say Hillary Clinton has "baggage" and is "divisive." Actually she has been investigated more thoroughly than almost anyone in the country\'s history and they found nothing at all. It isn\'t Hillary who is divisive, it\'s the people making all the accusations."'
```



## Using String and split

When you break a large string down into smaller chunks, or strings.





{:.input_area}
```python
sentence = "This is random text we’re going to split apart"
words = sentence.split(" ")
words
```





{:.output .output_data_text}
```
['This', 'is', 'random', 'text', 'we’re', 'going', 'to', 'split', 'apart']
```





{:.input_area}
```python
# Splitting speech by words
by_words = a_speech.split(' ')
```


## Counting words
A Counter is a dict subclass for counting. most_common() returns all elements in the counter.



{:.input_area}
```python
# Counting the number of words showed up in a speech
count_words_freq = Counter(by_words)
count_words_freq
```





{:.output .output_data_text}
```
Counter({'': 3,
         '"And': 1,
         '"Clinton': 1,
         '"How': 1,
         '"I\'m': 1,
         '"People': 1,
         '"Sitting': 1,
         '"an': 1,
         '"baggage"': 1,
         '"divisive."': 1,
         '"exciting";': 1,
         '"news': 1,
         '"profoundly': 1,
         '"remarkable";': 1,
         '"smart";': 1,
         '"top': 1,
         '"write': 1,
         "'08": 1,
         '(Dave': 1,
         '(Jerome': 1,
         '(To': 1,
         '(Yellow': 1,
         '(no': 1,
         '(nyceve)': 1,
         '-': 8,
         '10,000': 2,
         '100': 2,
         '2,200': 1,
         '22nd': 1,
         '6': 1,
         '6:00': 1,
         '7,700': 1,
         '7pm': 1,
         '=': 4,
         'A': 1,
         'Actually': 1,
         'After': 1,
         'And': 1,
         'Announcement': 1,
         'Armstrong)': 1,
         'BELTWAY': 1,
         'BLOG': 1,
         'Because': 1,
         'Bloggers': 1,
         'Blue)': 1,
         "Bush's": 1,
         'CARPETBAGGER': 1,
         'CONTEST': 1,
         'Campaign': 1,
         'Clinton': 7,
         "Clinton's": 2,
         'DAILY': 2,
         'DIARY': 2,
         'Demonstrating': 1,
         'Dog': 1,
         'EST': 1,
         'Edwards': 1,
         'FOREST': 1,
         'Give': 1,
         'Going': 1,
         'Hillary': 6,
         'Hours': 1,
         'I': 3,
         "I'm": 1,
         "I've": 1,
         'Indeed,': 1,
         'Instead': 1,
         'It': 2,
         'January': 1,
         'John': 1,
         'Johnson)': 1,
         'KOS': 2,
         'Kerry-2004': 1,
         'LEFT': 1,
         'Live:': 1,
         'MARSH': 1,
         'MESSAGES': 1,
         'MYDD': 1,
         'Monday,': 1,
         'Not': 3,
         'OF': 1,
         'OUTSIDE': 1,
         'Obama': 1,
         'Overwhelming': 1,
         'President': 1,
         'President.': 1,
         'REPORT': 1,
         'Rave': 1,
         'Response': 1,
         'Reviews:': 1,
         'Rodham': 1,
         'SEEING': 1,
         'SIGN': 1,
         'SIGN-UPS': 1,
         'SOTU': 1,
         'SUBMISSIONS': 1,
         'SUPPORT': 1,
         'Senate.': 1,
         'Senator': 3,
         'Senator,': 1,
         'TALK': 1,
         'TAYLOR': 1,
         'THE': 3,
         'The': 2,
         'UPS': 1,
         'VIDEO': 1,
         'WEBCAST': 1,
         'What': 1,
         'Within': 2,
         'a': 9,
         'a.m.)': 1,
         'about': 3,
         'accolades': 1,
         'accusations."': 1,
         'action': 1,
         'actual': 1,
         'add,': 1,
         'address."': 1,
         'admire': 1,
         'after': 1,
         'ago,': 1,
         'all': 2,
         'all.': 1,
         'almost': 2,
         'amount': 1,
         'an': 4,
         'and': 16,
         'announced': 1,
         'announcement': 4,
         'announcement.': 1,
         'any': 1,
         'anyone': 1,
         'appealing': 1,
         'armor.': 1,
         'around': 1,
         'as': 4,
         'at': 3,
         'attracted': 1,
         'becomes': 1,
         'been': 1,
         'beginning': 1,
         'being': 1,
         'bipartisan': 1,
         'blogger': 1,
         'bloggers': 1,
         'blogosphere,': 1,
         'brings': 1,
         'building': 1,
         'business': 1,
         'but': 1,
         'by': 5,
         'call': 1,
         'camp).': 1,
         'campaign': 1,
         'can': 1,
         'candidacy': 3,
         'candidacy,': 2,
         'candidate': 1,
         'chance': 1,
         'changed': 1,
         'clean,': 1,
         'collegiality': 1,
         'come.': 1,
         'concerns': 1,
         "country's": 1,
         'creates': 1,
         'day,': 1,
         'decades': 1,
         'divisive,': 1,
         "don't": 1,
         'done': 1,
         'doubt': 1,
         'doubt,': 1,
         'each': 1,
         'eight': 1,
         'email': 1,
         'emails': 1,
         'engaging': 1,
         'enormous': 1,
         'enters': 1,
         'enthusiasm': 1,
         'even': 2,
         'event': 1,
         'exciting': 1,
         'experience,': 1,
         'female': 1,
         'few': 1,
         'first': 2,
         'flocking': 1,
         'for': 7,
         'found': 1,
         'from': 2,
         'garnering': 2,
         'generated': 1,
         'generation"': 1,
         'generation."': 1,
         'getting': 2,
         'going': 1,
         'gone': 1,
         'got': 1,
         'groundswell': 1,
         'had': 1,
         'hailed': 1,
         'hard': 1,
         'has': 8,
         'have': 2,
         'heard': 1,
         'heavying': 1,
         'her': 11,
         'herself': 1,
         'historic': 1,
         'history': 1,
         'honest': 1,
         'hour.': 1,
         'hours': 2,
         "husband's": 1,
         'in': 5,
         'intelligence': 1,
         'interaction': 1,
         'internet': 2,
         'investigated': 1,
         'is': 4,
         "isn't": 1,
         'it': 2,
         "it's": 1,
         'it.': 1,
         'job': 1,
         'just': 4,
         'landscape': 1,
         'line,': 1,
         'lit': 1,
         'live': 1,
         'living': 1,
         'look': 1,
         'made': 1,
         'making': 1,
         'members': 1,
         'messages': 2,
         'minute': 1,
         'minute,': 1,
         'moderate': 1,
         'more': 2,
         'morning': 1,
         'moved': 1,
         'moving";': 1,
         'name': 1,
         'narrative': 1,
         'nearly': 1,
         'new': 1,
         'news': 1,
         'nights"': 1,
         'nothing': 1,
         'notify': 1,
         'now': 1,
         'of': 20,
         'on': 3,
         'one': 1,
         'online': 1,
         'online.': 1,
         'open': 1,
         'opponents.': 1,
         'our': 1,
         'out': 1,
         'outreach': 1,
         'outreach,': 1,
         'overwhelming': 1,
         'past': 1,
         'people': 1,
         'per': 2,
         'person,': 1,
         'personal': 1,
         'positioning': 1,
         'post"': 1,
         'power.': 1,
         'praise': 1,
         'president,': 1,
         'president....': 1,
         'presidential': 1,
         'press': 1,
         'previously': 1,
         'profoundly': 1,
         'public': 1,
         'puts': 1,
         'quick': 1,
         'race,': 1,
         'racks': 1,
         'rave': 1,
         'really': 1,
         'relationships': 1,
         'remarkable': 1,
         'reputation': 1,
         'response': 1,
         'reviews': 1,
         'room': 1,
         'run': 1,
         'savvy': 1,
         'say': 1,
         'separate': 1,
         'series': 1,
         'serious': 1,
         'setting,': 1,
         'several': 1,
         'shadow,': 1,
         'she': 4,
         'signs': 1,
         'simple': 1,
         'site': 2,
         'site,': 1,
         'six': 1,
         'smart': 1,
         'something': 1,
         'speculation,': 1,
         'statement': 1,
         'such': 1,
         'support': 1,
         'support,': 2,
         'supporters': 1,
         'survived': 1,
         'sympathy.': 1,
         'table."': 1,
         'takes': 1,
         'talent,': 1,
         'team': 1,
         'than': 2,
         'that': 2,
         'that."': 1,
         'the': 23,
         'them': 1,
         'these': 1,
         'they': 1,
         'this': 2,
         'thoroughly': 1,
         'thought,': 1,
         'thousands': 2,
         'three': 1,
         'thrived?': 1,
         'tier";': 1,
         'tier.': 1,
         'to': 8,
         'today,': 1,
         'top': 2,
         'touch."': 1,
         'tournament': 1,
         'unimaginable': 1,
         'unprecedented': 1,
         'up': 4,
         'using': 1,
         'various': 1,
         'video': 1,
         'was': 2,
         'we': 1,
         'web': 3,
         'webcasts': 1,
         'website': 1,
         'website.': 1,
         'week,': 1,
         'what': 1,
         'when': 1,
         'who': 1,
         'widespread': 1,
         'win.': 1,
         'winning,': 1,
         'with': 1,
         'within': 1,
         'without': 1,
         'woman': 1,
         'work': 1,
         'years': 2})
```





{:.input_area}
```python
# Guess what are the most frequent words in it
# Is it what you expected?
# Why? / Why not?
count_words_freq.most_common()
```





{:.output .output_data_text}
```
[('the', 23),
 ('of', 20),
 ('and', 16),
 ('her', 11),
 ('a', 9),
 ('to', 8),
 ('-', 8),
 ('has', 8),
 ('Clinton', 7),
 ('for', 7),
 ('Hillary', 6),
 ('by', 5),
 ('in', 5),
 ('up', 4),
 ('announcement', 4),
 ('as', 4),
 ('just', 4),
 ('=', 4),
 ('an', 4),
 ('is', 4),
 ('she', 4),
 ('web', 3),
 ('', 3),
 ('candidacy', 3),
 ('Senator', 3),
 ('on', 3),
 ('about', 3),
 ('at', 3),
 ('THE', 3),
 ('I', 3),
 ('Not', 3),
 ('site', 2),
 ('100', 2),
 ('per', 2),
 ('10,000', 2),
 ('messages', 2),
 ('hours', 2),
 ('candidacy,', 2),
 ("Clinton's", 2),
 ('internet', 2),
 ('garnering', 2),
 ('thousands', 2),
 ('Within', 2),
 ('support,', 2),
 ('was', 2),
 ('from', 2),
 ('The', 2),
 ('first', 2),
 ('DAILY', 2),
 ('KOS', 2),
 ('DIARY', 2),
 ('almost', 2),
 ('top', 2),
 ('all', 2),
 ('have', 2),
 ('that', 2),
 ('it', 2),
 ('this', 2),
 ('even', 2),
 ('It', 2),
 ('years', 2),
 ('getting', 2),
 ('more', 2),
 ('than', 2),
 ('Campaign', 1),
 ('signs', 1),
 ('new', 1),
 ('members', 1),
 ('minute,', 1),
 ('racks', 1),
 ('support', 1),
 ('within', 1),
 ('6', 1),
 ('hailed', 1),
 ('online', 1),
 ('"profoundly', 1),
 ('moving";', 1),
 ('"top', 1),
 ('tier";', 1),
 ('"exciting";', 1),
 ('"remarkable";', 1),
 ('"smart";', 1),
 ('"news', 1),
 ('generation"', 1),
 ('Demonstrating', 1),
 ('groundswell', 1),
 ('enthusiasm', 1),
 ('generated', 1),
 ('historic', 1),
 ('Rodham', 1),
 ('President', 1),
 ('lit', 1),
 ('today,', 1),
 ('rave', 1),
 ('reviews', 1),
 ('blogosphere,', 1),
 ('supporters', 1),
 ('flocking', 1),
 ('each', 1),
 ('hour.', 1),
 ('six', 1),
 ('going', 1),
 ('live', 1),
 ('campaign', 1),
 ('site,', 1),
 ('attracted', 1),
 ('widespread', 1),
 ('accolades', 1),
 ('online.', 1),
 ('Overwhelming', 1),
 ('Response', 1),
 ('Hours', 1),
 ('Going', 1),
 ('Live:', 1),
 ('SIGN', 1),
 ('UPS', 1),
 ('minute', 1),
 ('MESSAGES', 1),
 ('OF', 1),
 ('SUPPORT', 1),
 ('VIDEO', 1),
 ('WEBCAST', 1),
 ('SIGN-UPS', 1),
 ('7,700', 1),
 ('BLOG', 1),
 ('CONTEST', 1),
 ('SUBMISSIONS', 1),
 ('2,200', 1),
 ('Bloggers', 1),
 ('Give', 1),
 ('Announcement', 1),
 ('Rave', 1),
 ('Reviews:', 1),
 ('MYDD', 1),
 ('(Jerome', 1),
 ('Armstrong)', 1),
 ('"And', 1),
 ('blogger', 1),
 ('savvy', 1),
 ('John', 1),
 ('Edwards', 1),
 ('outreach,', 1),
 ('team', 1),
 ('had', 1),
 ('emails', 1),
 ('bloggers', 1),
 ('notify', 1),
 ('them', 1),
 ('separate', 1),
 ('press', 1),
 ('(no', 1),
 ('such', 1),
 ('outreach', 1),
 ('Obama', 1),
 ('camp).', 1),
 ('website', 1),
 ('clean,', 1),
 ('Kerry-2004', 1),
 ('look', 1),
 ('it.', 1),
 ('A', 1),
 ('smart', 1),
 ('"write', 1),
 ('our', 1),
 ('post"', 1),
 ('call', 1),
 ('action', 1),
 ('website.', 1),
 ('"an', 1),
 ('unprecedented', 1),
 ('series', 1),
 ('video', 1),
 ('webcasts', 1),
 ('beginning', 1),
 ('Monday,', 1),
 ('January', 1),
 ('22nd', 1),
 ('7pm', 1),
 ('EST', 1),
 ('three', 1),
 ('nights"', 1),
 ('creates', 1),
 ('quick', 1),
 ('narrative', 1),
 ('interaction', 1),
 ('response', 1),
 ('around', 1),
 ("Bush's", 1),
 ('SOTU', 1),
 ('address."', 1),
 ('(nyceve)', 1),
 ('"I\'m', 1),
 ('open', 1),
 ('honest', 1),
 ('person,', 1),
 ("I'm", 1),
 ('profoundly', 1),
 ('moved', 1),
 ('announcement.', 1),
 ('What', 1),
 ('unimaginable', 1),
 ('few', 1),
 ('decades', 1),
 ('ago,', 1),
 ('now', 1),
 ('something', 1),
 ('we', 1),
 ('can', 1),
 ('touch."', 1),
 ('CARPETBAGGER', 1),
 ('REPORT', 1),
 ('"Clinton', 1),
 ('enters', 1),
 ('race,', 1),
 ('without', 1),
 ('doubt,', 1),
 ('tier.', 1),
 ("I've", 1),
 ('heard', 1),
 ('various', 1),
 ('concerns', 1),
 ('but', 1),
 ("don't", 1),
 ('any', 1),
 ('doubt', 1),
 ('what', 1),
 ('takes', 1),
 ('win.', 1),
 ('Indeed,', 1),
 ('brings', 1),
 ('enormous', 1),
 ('amount', 1),
 ('talent,', 1),
 ('experience,', 1),
 ('intelligence', 1),
 ('table."', 1),
 ('TAYLOR', 1),
 ('MARSH', 1),
 ('"Sitting', 1),
 ('living', 1),
 ('room', 1),
 ('setting,', 1),
 ('made', 1),
 ('one', 1),
 ('simple', 1),
 ('statement', 1),
 ('changed', 1),
 ('landscape', 1),
 ("'08", 1),
 ('presidential', 1),
 ('tournament', 1),
 ('come.', 1),
 ('(To', 1),
 ('add,', 1),
 ('got', 1),
 ('email', 1),
 ('event', 1),
 ('morning', 1),
 ('after', 1),
 ('6:00', 1),
 ('a.m.)', 1),
 ('Because', 1),
 ('when', 1),
 ('woman', 1),
 ('run', 1),
 ('president,', 1),
 ('with', 1),
 ('actual', 1),
 ('chance', 1),
 ('winning,', 1),
 ('puts', 1),
 ('name', 1),
 ('reputation', 1),
 ('line,', 1),
 ('becomes', 1),
 ('news', 1),
 ('day,', 1),
 ('week,', 1),
 ('generation."', 1),
 ('TALK', 1),
 ('LEFT', 1),
 ('exciting', 1),
 ('serious', 1),
 ('female', 1),
 ('candidate', 1),
 ('President.', 1),
 ('OUTSIDE', 1),
 ('BELTWAY', 1),
 ('After', 1),
 ('nearly', 1),
 ('eight', 1),
 ('speculation,', 1),
 ('announced', 1),
 ('president....', 1),
 ('done', 1),
 ('remarkable', 1),
 ('job', 1),
 ('these', 1),
 ('past', 1),
 ('several', 1),
 ('out', 1),
 ("husband's", 1),
 ('shadow,', 1),
 ('positioning', 1),
 ('herself', 1),
 ('moderate', 1),
 ('previously', 1),
 ('thought,', 1),
 ('bipartisan', 1),
 ('praise', 1),
 ('collegiality', 1),
 ('hard', 1),
 ('work', 1),
 ('Senate.', 1),
 ('(Yellow', 1),
 ('Dog', 1),
 ('Blue)', 1),
 ('"How', 1),
 ('survived', 1),
 ('thrived?', 1),
 ('heavying', 1),
 ('armor.', 1),
 ('engaging', 1),
 ('overwhelming', 1),
 ('opponents.', 1),
 ('appealing', 1),
 ('public', 1),
 ('sympathy.', 1),
 ('Instead', 1),
 ('gone', 1),
 ('business', 1),
 ('being', 1),
 ('Senator,', 1),
 ('building', 1),
 ('personal', 1),
 ('relationships', 1),
 ('using', 1),
 ('power.', 1),
 ('And', 1),
 ('really', 1),
 ('admire', 1),
 ('that."', 1),
 ('SEEING', 1),
 ('FOREST', 1),
 ('(Dave', 1),
 ('Johnson)', 1),
 ('"People', 1),
 ('say', 1),
 ('"baggage"', 1),
 ('"divisive."', 1),
 ('Actually', 1),
 ('been', 1),
 ('investigated', 1),
 ('thoroughly', 1),
 ('anyone', 1),
 ("country's", 1),
 ('history', 1),
 ('they', 1),
 ('found', 1),
 ('nothing', 1),
 ('all.', 1),
 ("isn't", 1),
 ('who', 1),
 ('divisive,', 1),
 ("it's", 1),
 ('people', 1),
 ('making', 1),
 ('accusations."', 1)]
```



## Data Processing

Some libraries are huge. It takes time to retrieve the data from the libraries.
So we prepared stopwords from  "from nltk.corpus import stopwords".

A **stopword** is a word that is often filtered out during text processing. Stopwords are usually common function words, like 'the', 'a', or 'and'. These words are used frequently but aren't very informative. Filtering them out results in more informative and interesting analysis.



{:.input_area}
```python
# stop_words = set(stopwords.words("english"))
with open('stopwords.json') as json_data:
    stop_words_json = json.load(json_data)
    
# with open('foundations_dict.json') as json_data:
#     mft_dict = json.load(json_data)
stop_words = stop_words_json['words']
stop_words
```





{:.output .output_data_text}
```
['a',
 'about',
 'above',
 'after',
 'again',
 'against',
 'ain',
 'all',
 'am',
 'an',
 'and',
 'any',
 'are',
 'aren',
 'as',
 'at',
 'be',
 'because',
 'been',
 'before',
 'being',
 'below',
 'between',
 'both',
 'but',
 'by',
 'can',
 'couldn',
 'd',
 'did',
 'didn',
 'do',
 'does',
 'doesn',
 'doing',
 'don',
 'down',
 'during',
 'each',
 'few',
 'for',
 'from',
 'further',
 'had',
 'hadn',
 'has',
 'hasn',
 'have',
 'haven',
 'having',
 'he',
 'her',
 'here',
 'hers',
 'herself',
 'him',
 'himself',
 'his',
 'how',
 'i',
 'if',
 'in',
 'into',
 'is',
 'isn',
 'it',
 'its',
 'itself',
 'just',
 'll',
 'm',
 'ma',
 'me',
 'mightn',
 'more',
 'most',
 'mustn',
 'my',
 'myself',
 'needn',
 'no',
 'nor',
 'not',
 'now',
 'o',
 'of',
 'off',
 'on',
 'once',
 'only',
 'or',
 'other',
 'our',
 'ours',
 'ourselves',
 'out',
 'over',
 'own',
 're',
 's',
 'same',
 'shan',
 'she',
 'should',
 'shouldn',
 'so',
 'some',
 'such',
 't',
 'than',
 'that',
 'the',
 'their',
 'theirs',
 'them',
 'themselves',
 'then',
 'there',
 'these',
 'they',
 'this',
 'those',
 'through',
 'to',
 'too',
 'under',
 'until',
 'up',
 've',
 'very',
 'was',
 'wasn',
 'we',
 'were',
 'weren',
 'what',
 'when',
 'where',
 'which',
 'while',
 'who',
 'whom',
 'why',
 'will',
 'with',
 'won',
 'wouldn',
 'y',
 'you',
 'your',
 'yours',
 'yourself',
 'yourselves']
```



### Functions

Here are simple rules to define a function in Python. 

Function blocks begin with the keyword `def` followed by the function name and parentheses ( ( ) ). 

Any input parameters or arguments should be placed within these parentheses. You can also define parameters inside these parentheses.

Function definitions consist of a def statement that indicates a `<name>` and a comma-separated list of named `<formal parameters>`, then a return statement, called the function body, that specifies the `<return expression>` of the function, which is an expression to be evaluated whenever the function is applied:





{:.input_area}
```python
# def <name>(<formal parameters>):
#    return <return expression>
```




{:.input_area}
```python
def three():
    return 3

three()
```





{:.output .output_data_text}
```
3
```



The second line must be indented — most programmers use four spaces to indent. The return expression is not evaluated right away; it is stored as part of the newly defined function and evaluated only when the function is eventually applied.

I defined a function whose name is without_stopwords. I will explain how this works. However, it is okay for you not to understand the details of the code inside the function. All you have to know is what the function does and how to use it.



{:.input_area}
```python
def without_stopwords(a_speech):
    """ input(a_speech): string type of a speech
        output : list of words in the speech without stop words
        
        >>> exstr = "This is an example showing off stop word filter"
        >>> without_stopwords(exstr)
        ... ['This', 'example', 'showing', 'stop', 'word', 'filter']
    """
    a_speech = word_tokenize(a_speech)
    filtered = []
    #this is for-loop and it makes program repeat the following lines of code.
    for word in a_speech:
        #if is conditional statement that makes program execute the code when the condition is true.
        if word not in stop_words:
            filtered.append(word)
    return filtered
```




{:.input_area}
```python
exstr = "This is an example showing off stop word filter"
```




{:.input_area}
```python
without_stopwords(exstr)
```





{:.output .output_data_text}
```
['This', 'example', 'showing', 'stop', 'word', 'filter']
```





{:.input_area}
```python
a_speech
```





{:.output .output_data_text}
```
'Campaign web site signs up 100 new members per minute, racks up 10,000 messages of support within 6 hours of announcement  Clinton candidacy hailed online as "profoundly moving"; "top tier"; "exciting"; "remarkable"; "smart"; and "news of a generation" Demonstrating the groundswell of enthusiasm generated by her historic candidacy, Senator Hillary Rodham Clinton\'s announcement for President lit up the internet today, garnering rave reviews in the blogosphere, and thousands of supporters flocking to her web site each hour. Within just six hours of the announcement going live on her campaign web site, Senator Clinton\'s candidacy attracted thousands of messages of support, and widespread accolades online. Overwhelming Response Within Hours of Going Live:  SIGN UPS = 100 per minute MESSAGES OF SUPPORT = 10,000 VIDEO WEBCAST SIGN-UPS = 7,700 BLOG CONTEST SUBMISSIONS = 2,200  Bloggers Give Clinton Announcement Rave Reviews: MYDD (Jerome Armstrong) - "And as blogger savvy as John Edwards was in outreach, Clinton internet team had the emails of bloggers to notify them separate from the press (no such outreach from the Obama camp). The website has the clean, Kerry-2004 look about it. A smart "write our first post" call to action on the website. The announcement of "an unprecedented series of video webcasts beginning Monday, January 22nd at 7pm EST for three nights" creates a quick narrative of interaction and response around Bush\'s SOTU address." DAILY KOS DIARY (nyceve) - "I\'m an open and honest person, and I\'m profoundly moved by her announcement. What was unimaginable just a few decades ago, is now something we can almost touch." THE CARPETBAGGER REPORT - "Clinton enters the race, without a doubt, at the top of the top tier. I\'ve heard all the various concerns about her candidacy, but I don\'t have any doubt that she has what it takes to win. Indeed, Clinton brings an enormous amount of talent, experience, and intelligence to the table." TAYLOR MARSH - "Sitting in a living room setting, Senator Hillary Clinton made one simple statement that changed the landscape of the \'08 presidential tournament to come. (To add, I got an email about this event this morning just after 6:00 a.m.) Because when the first woman to run for president, with an actual chance of winning, puts her name and reputation on the line, it becomes news of the day, week, even a generation." TALK LEFT - It is exciting to have a serious female candidate for President. OUTSIDE THE BELTWAY - After nearly eight years of speculation, Hillary Clinton has announced her candidacy for president.... she has done a remarkable job these past several years getting out of her husband\'s shadow, positioning herself as more moderate than previously thought, and garnering bipartisan praise for collegiality and hard work in the Senate. DAILY KOS DIARY (Yellow Dog Blue) - "How has she survived and thrived? Not by heavying up her armor. Not by engaging and overwhelming her opponents. Not even by appealing for public sympathy. Instead Hillary has just gone her business being a Senator, building personal relationships and support, getting and using power. And I really admire that." SEEING THE FOREST (Dave Johnson) - "People say Hillary Clinton has "baggage" and is "divisive." Actually she has been investigated more thoroughly than almost anyone in the country\'s history and they found nothing at all. It isn\'t Hillary who is divisive, it\'s the people making all the accusations."'
```





{:.input_area}
```python
without_stopwords(a_speech)
```





{:.output .output_data_text}
```
['Campaign',
 'web',
 'site',
 'signs',
 '100',
 'new',
 'members',
 'per',
 'minute',
 ',',
 'racks',
 '10,000',
 'messages',
 'support',
 'within',
 '6',
 'hours',
 'announcement',
 'Clinton',
 'candidacy',
 'hailed',
 'online',
 '``',
 'profoundly',
 'moving',
 "''",
 ';',
 '``',
 'top',
 'tier',
 "''",
 ';',
 '``',
 'exciting',
 "''",
 ';',
 '``',
 'remarkable',
 "''",
 ';',
 '``',
 'smart',
 "''",
 ';',
 '``',
 'news',
 'generation',
 "''",
 'Demonstrating',
 'groundswell',
 'enthusiasm',
 'generated',
 'historic',
 'candidacy',
 ',',
 'Senator',
 'Hillary',
 'Rodham',
 'Clinton',
 "'s",
 'announcement',
 'President',
 'lit',
 'internet',
 'today',
 ',',
 'garnering',
 'rave',
 'reviews',
 'blogosphere',
 ',',
 'thousands',
 'supporters',
 'flocking',
 'web',
 'site',
 'hour',
 '.',
 'Within',
 'six',
 'hours',
 'announcement',
 'going',
 'live',
 'campaign',
 'web',
 'site',
 ',',
 'Senator',
 'Clinton',
 "'s",
 'candidacy',
 'attracted',
 'thousands',
 'messages',
 'support',
 ',',
 'widespread',
 'accolades',
 'online',
 '.',
 'Overwhelming',
 'Response',
 'Within',
 'Hours',
 'Going',
 'Live',
 ':',
 'SIGN',
 'UPS',
 '=',
 '100',
 'per',
 'minute',
 'MESSAGES',
 'OF',
 'SUPPORT',
 '=',
 '10,000',
 'VIDEO',
 'WEBCAST',
 'SIGN-UPS',
 '=',
 '7,700',
 'BLOG',
 'CONTEST',
 'SUBMISSIONS',
 '=',
 '2,200',
 'Bloggers',
 'Give',
 'Clinton',
 'Announcement',
 'Rave',
 'Reviews',
 ':',
 'MYDD',
 '(',
 'Jerome',
 'Armstrong',
 ')',
 '-',
 '``',
 'And',
 'blogger',
 'savvy',
 'John',
 'Edwards',
 'outreach',
 ',',
 'Clinton',
 'internet',
 'team',
 'emails',
 'bloggers',
 'notify',
 'separate',
 'press',
 '(',
 'outreach',
 'Obama',
 'camp',
 ')',
 '.',
 'The',
 'website',
 'clean',
 ',',
 'Kerry-2004',
 'look',
 '.',
 'A',
 'smart',
 '``',
 'write',
 'first',
 'post',
 "''",
 'call',
 'action',
 'website',
 '.',
 'The',
 'announcement',
 '``',
 'unprecedented',
 'series',
 'video',
 'webcasts',
 'beginning',
 'Monday',
 ',',
 'January',
 '22nd',
 '7pm',
 'EST',
 'three',
 'nights',
 "''",
 'creates',
 'quick',
 'narrative',
 'interaction',
 'response',
 'around',
 'Bush',
 "'s",
 'SOTU',
 'address',
 '.',
 "''",
 'DAILY',
 'KOS',
 'DIARY',
 '(',
 'nyceve',
 ')',
 '-',
 '``',
 'I',
 "'m",
 'open',
 'honest',
 'person',
 ',',
 'I',
 "'m",
 'profoundly',
 'moved',
 'announcement',
 '.',
 'What',
 'unimaginable',
 'decades',
 'ago',
 ',',
 'something',
 'almost',
 'touch',
 '.',
 "''",
 'THE',
 'CARPETBAGGER',
 'REPORT',
 '-',
 '``',
 'Clinton',
 'enters',
 'race',
 ',',
 'without',
 'doubt',
 ',',
 'top',
 'top',
 'tier',
 '.',
 'I',
 "'ve",
 'heard',
 'various',
 'concerns',
 'candidacy',
 ',',
 'I',
 "n't",
 'doubt',
 'takes',
 'win',
 '.',
 'Indeed',
 ',',
 'Clinton',
 'brings',
 'enormous',
 'amount',
 'talent',
 ',',
 'experience',
 ',',
 'intelligence',
 'table',
 '.',
 "''",
 'TAYLOR',
 'MARSH',
 '-',
 '``',
 'Sitting',
 'living',
 'room',
 'setting',
 ',',
 'Senator',
 'Hillary',
 'Clinton',
 'made',
 'one',
 'simple',
 'statement',
 'changed',
 'landscape',
 "'08",
 'presidential',
 'tournament',
 'come',
 '.',
 '(',
 'To',
 'add',
 ',',
 'I',
 'got',
 'email',
 'event',
 'morning',
 '6:00',
 'a.m.',
 ')',
 'Because',
 'first',
 'woman',
 'run',
 'president',
 ',',
 'actual',
 'chance',
 'winning',
 ',',
 'puts',
 'name',
 'reputation',
 'line',
 ',',
 'becomes',
 'news',
 'day',
 ',',
 'week',
 ',',
 'even',
 'generation',
 '.',
 "''",
 'TALK',
 'LEFT',
 '-',
 'It',
 'exciting',
 'serious',
 'female',
 'candidate',
 'President',
 '.',
 'OUTSIDE',
 'THE',
 'BELTWAY',
 '-',
 'After',
 'nearly',
 'eight',
 'years',
 'speculation',
 ',',
 'Hillary',
 'Clinton',
 'announced',
 'candidacy',
 'president',
 '...',
 '.',
 'done',
 'remarkable',
 'job',
 'past',
 'several',
 'years',
 'getting',
 'husband',
 "'s",
 'shadow',
 ',',
 'positioning',
 'moderate',
 'previously',
 'thought',
 ',',
 'garnering',
 'bipartisan',
 'praise',
 'collegiality',
 'hard',
 'work',
 'Senate',
 '.',
 'DAILY',
 'KOS',
 'DIARY',
 '(',
 'Yellow',
 'Dog',
 'Blue',
 ')',
 '-',
 '``',
 'How',
 'survived',
 'thrived',
 '?',
 'Not',
 'heavying',
 'armor',
 '.',
 'Not',
 'engaging',
 'overwhelming',
 'opponents',
 '.',
 'Not',
 'even',
 'appealing',
 'public',
 'sympathy',
 '.',
 'Instead',
 'Hillary',
 'gone',
 'business',
 'Senator',
 ',',
 'building',
 'personal',
 'relationships',
 'support',
 ',',
 'getting',
 'using',
 'power',
 '.',
 'And',
 'I',
 'really',
 'admire',
 '.',
 "''",
 'SEEING',
 'THE',
 'FOREST',
 '(',
 'Dave',
 'Johnson',
 ')',
 '-',
 '``',
 'People',
 'say',
 'Hillary',
 'Clinton',
 '``',
 'baggage',
 "''",
 '``',
 'divisive',
 '.',
 "''",
 'Actually',
 'investigated',
 'thoroughly',
 'almost',
 'anyone',
 'country',
 "'s",
 'history',
 'found',
 'nothing',
 '.',
 'It',
 "n't",
 'Hillary',
 'divisive',
 ',',
 "'s",
 'people',
 'making',
 'accusations',
 '.',
 "''"]
```





{:.input_area}
```python
list_of_words_c = without_stopwords(a_speech)
```




{:.input_area}
```python
Counter(list_of_words_c).most_common()
```





{:.output .output_data_text}
```
[(',', 30),
 ('.', 24),
 ('``', 16),
 ("''", 16),
 ('Clinton', 10),
 ('-', 8),
 ('Hillary', 6),
 ("'s", 6),
 ('(', 6),
 (')', 6),
 ('I', 6),
 ('announcement', 5),
 ('candidacy', 5),
 (';', 5),
 ('Senator', 4),
 ('=', 4),
 ('web', 3),
 ('site', 3),
 ('support', 3),
 ('top', 3),
 ('THE', 3),
 ('Not', 3),
 ('100', 2),
 ('per', 2),
 ('minute', 2),
 ('10,000', 2),
 ('messages', 2),
 ('hours', 2),
 ('online', 2),
 ('profoundly', 2),
 ('tier', 2),
 ('exciting', 2),
 ('remarkable', 2),
 ('smart', 2),
 ('news', 2),
 ('generation', 2),
 ('President', 2),
 ('internet', 2),
 ('garnering', 2),
 ('thousands', 2),
 ('Within', 2),
 (':', 2),
 ('And', 2),
 ('outreach', 2),
 ('The', 2),
 ('website', 2),
 ('first', 2),
 ('DAILY', 2),
 ('KOS', 2),
 ('DIARY', 2),
 ("'m", 2),
 ('almost', 2),
 ('doubt', 2),
 ("n't", 2),
 ('president', 2),
 ('even', 2),
 ('It', 2),
 ('years', 2),
 ('getting', 2),
 ('divisive', 2),
 ('Campaign', 1),
 ('signs', 1),
 ('new', 1),
 ('members', 1),
 ('racks', 1),
 ('within', 1),
 ('6', 1),
 ('hailed', 1),
 ('moving', 1),
 ('Demonstrating', 1),
 ('groundswell', 1),
 ('enthusiasm', 1),
 ('generated', 1),
 ('historic', 1),
 ('Rodham', 1),
 ('lit', 1),
 ('today', 1),
 ('rave', 1),
 ('reviews', 1),
 ('blogosphere', 1),
 ('supporters', 1),
 ('flocking', 1),
 ('hour', 1),
 ('six', 1),
 ('going', 1),
 ('live', 1),
 ('campaign', 1),
 ('attracted', 1),
 ('widespread', 1),
 ('accolades', 1),
 ('Overwhelming', 1),
 ('Response', 1),
 ('Hours', 1),
 ('Going', 1),
 ('Live', 1),
 ('SIGN', 1),
 ('UPS', 1),
 ('MESSAGES', 1),
 ('OF', 1),
 ('SUPPORT', 1),
 ('VIDEO', 1),
 ('WEBCAST', 1),
 ('SIGN-UPS', 1),
 ('7,700', 1),
 ('BLOG', 1),
 ('CONTEST', 1),
 ('SUBMISSIONS', 1),
 ('2,200', 1),
 ('Bloggers', 1),
 ('Give', 1),
 ('Announcement', 1),
 ('Rave', 1),
 ('Reviews', 1),
 ('MYDD', 1),
 ('Jerome', 1),
 ('Armstrong', 1),
 ('blogger', 1),
 ('savvy', 1),
 ('John', 1),
 ('Edwards', 1),
 ('team', 1),
 ('emails', 1),
 ('bloggers', 1),
 ('notify', 1),
 ('separate', 1),
 ('press', 1),
 ('Obama', 1),
 ('camp', 1),
 ('clean', 1),
 ('Kerry-2004', 1),
 ('look', 1),
 ('A', 1),
 ('write', 1),
 ('post', 1),
 ('call', 1),
 ('action', 1),
 ('unprecedented', 1),
 ('series', 1),
 ('video', 1),
 ('webcasts', 1),
 ('beginning', 1),
 ('Monday', 1),
 ('January', 1),
 ('22nd', 1),
 ('7pm', 1),
 ('EST', 1),
 ('three', 1),
 ('nights', 1),
 ('creates', 1),
 ('quick', 1),
 ('narrative', 1),
 ('interaction', 1),
 ('response', 1),
 ('around', 1),
 ('Bush', 1),
 ('SOTU', 1),
 ('address', 1),
 ('nyceve', 1),
 ('open', 1),
 ('honest', 1),
 ('person', 1),
 ('moved', 1),
 ('What', 1),
 ('unimaginable', 1),
 ('decades', 1),
 ('ago', 1),
 ('something', 1),
 ('touch', 1),
 ('CARPETBAGGER', 1),
 ('REPORT', 1),
 ('enters', 1),
 ('race', 1),
 ('without', 1),
 ("'ve", 1),
 ('heard', 1),
 ('various', 1),
 ('concerns', 1),
 ('takes', 1),
 ('win', 1),
 ('Indeed', 1),
 ('brings', 1),
 ('enormous', 1),
 ('amount', 1),
 ('talent', 1),
 ('experience', 1),
 ('intelligence', 1),
 ('table', 1),
 ('TAYLOR', 1),
 ('MARSH', 1),
 ('Sitting', 1),
 ('living', 1),
 ('room', 1),
 ('setting', 1),
 ('made', 1),
 ('one', 1),
 ('simple', 1),
 ('statement', 1),
 ('changed', 1),
 ('landscape', 1),
 ("'08", 1),
 ('presidential', 1),
 ('tournament', 1),
 ('come', 1),
 ('To', 1),
 ('add', 1),
 ('got', 1),
 ('email', 1),
 ('event', 1),
 ('morning', 1),
 ('6:00', 1),
 ('a.m.', 1),
 ('Because', 1),
 ('woman', 1),
 ('run', 1),
 ('actual', 1),
 ('chance', 1),
 ('winning', 1),
 ('puts', 1),
 ('name', 1),
 ('reputation', 1),
 ('line', 1),
 ('becomes', 1),
 ('day', 1),
 ('week', 1),
 ('TALK', 1),
 ('LEFT', 1),
 ('serious', 1),
 ('female', 1),
 ('candidate', 1),
 ('OUTSIDE', 1),
 ('BELTWAY', 1),
 ('After', 1),
 ('nearly', 1),
 ('eight', 1),
 ('speculation', 1),
 ('announced', 1),
 ('...', 1),
 ('done', 1),
 ('job', 1),
 ('past', 1),
 ('several', 1),
 ('husband', 1),
 ('shadow', 1),
 ('positioning', 1),
 ('moderate', 1),
 ('previously', 1),
 ('thought', 1),
 ('bipartisan', 1),
 ('praise', 1),
 ('collegiality', 1),
 ('hard', 1),
 ('work', 1),
 ('Senate', 1),
 ('Yellow', 1),
 ('Dog', 1),
 ('Blue', 1),
 ('How', 1),
 ('survived', 1),
 ('thrived', 1),
 ('?', 1),
 ('heavying', 1),
 ('armor', 1),
 ('engaging', 1),
 ('overwhelming', 1),
 ('opponents', 1),
 ('appealing', 1),
 ('public', 1),
 ('sympathy', 1),
 ('Instead', 1),
 ('gone', 1),
 ('business', 1),
 ('building', 1),
 ('personal', 1),
 ('relationships', 1),
 ('using', 1),
 ('power', 1),
 ('really', 1),
 ('admire', 1),
 ('SEEING', 1),
 ('FOREST', 1),
 ('Dave', 1),
 ('Johnson', 1),
 ('People', 1),
 ('say', 1),
 ('baggage', 1),
 ('Actually', 1),
 ('investigated', 1),
 ('thoroughly', 1),
 ('anyone', 1),
 ('country', 1),
 ('history', 1),
 ('found', 1),
 ('nothing', 1),
 ('people', 1),
 ('making', 1),
 ('accusations', 1)]
```



The function below is to filter special characters, such as commas, quotes, colons and so on.



{:.input_area}
```python
def without_words_set(a_speech, a_set):
    a_speech = word_tokenize(a_speech)
    filtered = []
    for word in a_speech:
        if word not in a_set:
            filtered.append(word)
    return filtered
```




{:.input_area}
```python
stop_words_set = set(stop_words)
```




{:.input_area}
```python
filter_set = {',', '.', '1', '(', ')','*',':','2', '\'', ';', '?', '=','-', '``', "''"}
```




{:.input_area}
```python
custom_filter = stop_words_set | filter_set
```




{:.input_area}
```python
custom_filter
```





{:.output .output_data_text}
```
{"'",
 "''",
 '(',
 ')',
 '*',
 ',',
 '-',
 '.',
 '1',
 '2',
 ':',
 ';',
 '=',
 '?',
 '``',
 'a',
 'about',
 'above',
 'after',
 'again',
 'against',
 'ain',
 'all',
 'am',
 'an',
 'and',
 'any',
 'are',
 'aren',
 'as',
 'at',
 'be',
 'because',
 'been',
 'before',
 'being',
 'below',
 'between',
 'both',
 'but',
 'by',
 'can',
 'couldn',
 'd',
 'did',
 'didn',
 'do',
 'does',
 'doesn',
 'doing',
 'don',
 'down',
 'during',
 'each',
 'few',
 'for',
 'from',
 'further',
 'had',
 'hadn',
 'has',
 'hasn',
 'have',
 'haven',
 'having',
 'he',
 'her',
 'here',
 'hers',
 'herself',
 'him',
 'himself',
 'his',
 'how',
 'i',
 'if',
 'in',
 'into',
 'is',
 'isn',
 'it',
 'its',
 'itself',
 'just',
 'll',
 'm',
 'ma',
 'me',
 'mightn',
 'more',
 'most',
 'mustn',
 'my',
 'myself',
 'needn',
 'no',
 'nor',
 'not',
 'now',
 'o',
 'of',
 'off',
 'on',
 'once',
 'only',
 'or',
 'other',
 'our',
 'ours',
 'ourselves',
 'out',
 'over',
 'own',
 're',
 's',
 'same',
 'shan',
 'she',
 'should',
 'shouldn',
 'so',
 'some',
 'such',
 't',
 'than',
 'that',
 'the',
 'their',
 'theirs',
 'them',
 'themselves',
 'then',
 'there',
 'these',
 'they',
 'this',
 'those',
 'through',
 'to',
 'too',
 'under',
 'until',
 'up',
 've',
 'very',
 'was',
 'wasn',
 'we',
 'were',
 'weren',
 'what',
 'when',
 'where',
 'which',
 'while',
 'who',
 'whom',
 'why',
 'will',
 'with',
 'won',
 'wouldn',
 'y',
 'you',
 'your',
 'yours',
 'yourself',
 'yourselves'}
```





{:.input_area}
```python
filtered = without_words_set(a_speech, custom_filter)
filtered
```





{:.output .output_data_text}
```
['Campaign',
 'web',
 'site',
 'signs',
 '100',
 'new',
 'members',
 'per',
 'minute',
 'racks',
 '10,000',
 'messages',
 'support',
 'within',
 '6',
 'hours',
 'announcement',
 'Clinton',
 'candidacy',
 'hailed',
 'online',
 'profoundly',
 'moving',
 'top',
 'tier',
 'exciting',
 'remarkable',
 'smart',
 'news',
 'generation',
 'Demonstrating',
 'groundswell',
 'enthusiasm',
 'generated',
 'historic',
 'candidacy',
 'Senator',
 'Hillary',
 'Rodham',
 'Clinton',
 "'s",
 'announcement',
 'President',
 'lit',
 'internet',
 'today',
 'garnering',
 'rave',
 'reviews',
 'blogosphere',
 'thousands',
 'supporters',
 'flocking',
 'web',
 'site',
 'hour',
 'Within',
 'six',
 'hours',
 'announcement',
 'going',
 'live',
 'campaign',
 'web',
 'site',
 'Senator',
 'Clinton',
 "'s",
 'candidacy',
 'attracted',
 'thousands',
 'messages',
 'support',
 'widespread',
 'accolades',
 'online',
 'Overwhelming',
 'Response',
 'Within',
 'Hours',
 'Going',
 'Live',
 'SIGN',
 'UPS',
 '100',
 'per',
 'minute',
 'MESSAGES',
 'OF',
 'SUPPORT',
 '10,000',
 'VIDEO',
 'WEBCAST',
 'SIGN-UPS',
 '7,700',
 'BLOG',
 'CONTEST',
 'SUBMISSIONS',
 '2,200',
 'Bloggers',
 'Give',
 'Clinton',
 'Announcement',
 'Rave',
 'Reviews',
 'MYDD',
 'Jerome',
 'Armstrong',
 'And',
 'blogger',
 'savvy',
 'John',
 'Edwards',
 'outreach',
 'Clinton',
 'internet',
 'team',
 'emails',
 'bloggers',
 'notify',
 'separate',
 'press',
 'outreach',
 'Obama',
 'camp',
 'The',
 'website',
 'clean',
 'Kerry-2004',
 'look',
 'A',
 'smart',
 'write',
 'first',
 'post',
 'call',
 'action',
 'website',
 'The',
 'announcement',
 'unprecedented',
 'series',
 'video',
 'webcasts',
 'beginning',
 'Monday',
 'January',
 '22nd',
 '7pm',
 'EST',
 'three',
 'nights',
 'creates',
 'quick',
 'narrative',
 'interaction',
 'response',
 'around',
 'Bush',
 "'s",
 'SOTU',
 'address',
 'DAILY',
 'KOS',
 'DIARY',
 'nyceve',
 'I',
 "'m",
 'open',
 'honest',
 'person',
 'I',
 "'m",
 'profoundly',
 'moved',
 'announcement',
 'What',
 'unimaginable',
 'decades',
 'ago',
 'something',
 'almost',
 'touch',
 'THE',
 'CARPETBAGGER',
 'REPORT',
 'Clinton',
 'enters',
 'race',
 'without',
 'doubt',
 'top',
 'top',
 'tier',
 'I',
 "'ve",
 'heard',
 'various',
 'concerns',
 'candidacy',
 'I',
 "n't",
 'doubt',
 'takes',
 'win',
 'Indeed',
 'Clinton',
 'brings',
 'enormous',
 'amount',
 'talent',
 'experience',
 'intelligence',
 'table',
 'TAYLOR',
 'MARSH',
 'Sitting',
 'living',
 'room',
 'setting',
 'Senator',
 'Hillary',
 'Clinton',
 'made',
 'one',
 'simple',
 'statement',
 'changed',
 'landscape',
 "'08",
 'presidential',
 'tournament',
 'come',
 'To',
 'add',
 'I',
 'got',
 'email',
 'event',
 'morning',
 '6:00',
 'a.m.',
 'Because',
 'first',
 'woman',
 'run',
 'president',
 'actual',
 'chance',
 'winning',
 'puts',
 'name',
 'reputation',
 'line',
 'becomes',
 'news',
 'day',
 'week',
 'even',
 'generation',
 'TALK',
 'LEFT',
 'It',
 'exciting',
 'serious',
 'female',
 'candidate',
 'President',
 'OUTSIDE',
 'THE',
 'BELTWAY',
 'After',
 'nearly',
 'eight',
 'years',
 'speculation',
 'Hillary',
 'Clinton',
 'announced',
 'candidacy',
 'president',
 '...',
 'done',
 'remarkable',
 'job',
 'past',
 'several',
 'years',
 'getting',
 'husband',
 "'s",
 'shadow',
 'positioning',
 'moderate',
 'previously',
 'thought',
 'garnering',
 'bipartisan',
 'praise',
 'collegiality',
 'hard',
 'work',
 'Senate',
 'DAILY',
 'KOS',
 'DIARY',
 'Yellow',
 'Dog',
 'Blue',
 'How',
 'survived',
 'thrived',
 'Not',
 'heavying',
 'armor',
 'Not',
 'engaging',
 'overwhelming',
 'opponents',
 'Not',
 'even',
 'appealing',
 'public',
 'sympathy',
 'Instead',
 'Hillary',
 'gone',
 'business',
 'Senator',
 'building',
 'personal',
 'relationships',
 'support',
 'getting',
 'using',
 'power',
 'And',
 'I',
 'really',
 'admire',
 'SEEING',
 'THE',
 'FOREST',
 'Dave',
 'Johnson',
 'People',
 'say',
 'Hillary',
 'Clinton',
 'baggage',
 'divisive',
 'Actually',
 'investigated',
 'thoroughly',
 'almost',
 'anyone',
 'country',
 "'s",
 'history',
 'found',
 'nothing',
 'It',
 "n't",
 'Hillary',
 'divisive',
 "'s",
 'people',
 'making',
 'accusations']
```





{:.input_area}
```python
Counter(filtered).most_common(15)
```





{:.output .output_data_text}
```
[('Clinton', 10),
 ('Hillary', 6),
 ("'s", 6),
 ('I', 6),
 ('announcement', 5),
 ('candidacy', 5),
 ('Senator', 4),
 ('web', 3),
 ('site', 3),
 ('support', 3),
 ('top', 3),
 ('THE', 3),
 ('Not', 3),
 ('100', 2),
 ('per', 2)]
```



## Counts words 2
Build your own dictionary you want to count and run it



{:.input_area}
```python
def words_to_dictionary(words):
    """Making a dictionary with given words. 
    Set key as each word and set value to initail counting 0"""
    dic = {}
    for word in words:
        dic[word] = 0
    return dic
```




{:.input_area}
```python
my_words = ["Clinton", "Hillary", "action", "her"]
my_dictionary = words_to_dictionary(my_words)
my_dictionary
```





{:.output .output_data_text}
```
{'Clinton': 0, 'Hillary': 0, 'action': 0, 'her': 0}
```





{:.input_area}
```python
def count_words(dictionary, speech):
    speech_words = speech.split(' ')
    for word in speech_words:
        if word in dictionary:
            dictionary[word] = dictionary[word] + 1
    return dictionary
count_words(my_dictionary, a_speech)
```





{:.output .output_data_text}
```
{'Clinton': 7, 'Hillary': 6, 'action': 1, 'her': 11}
```



### Assignment: Code your dictionary into Python

First, make a list of the words you found corresponding to each foundation. Assign them to the variable names below by filling in the lists.



{:.input_area}
```python
# Make 6 lists. 
# Tip: each word needs to go in quotation marks and each string must be separated by commas
care_words = []
authority_words = []
loyalty_words = []
sanctity_words = []
fairness_words = []
liberty_words = []

```


Next, make your dictionary by creating a new dictionary with the foundations as keys and your lists as the values.



{:.input_area}
```python
# 
my_dict = {'test': 1}
```


Finally, run the next cell to write your dictionary to a file.



{:.input_area}
```python
# Run this cell to write dictionary to a file
import json 
# convert dictionary to a JSON-formatted string
with open('../mft_data/my_dict.json', 'w') as fp:
    json.dump(my_dict, fp, sort_keys=True, indent=4)
```


## Next Steps

### Homework!
Complete this short assignment by Monday. We recommend starting early, and coming to office hours for help. https://tinyurl.com/rhetorichomework

### Office Hours
Come to the Center for Connected Learning on the first floor of Moffitt Library (opposite side of elevators) today from 4:30-6:00 pm to answer any questions relating to this notebook or the homework.

### Next Week
#### Module 02: Moral Foundations Analysis
#### Module 03: The Rhetoric of Data

Module Developers: Alec Kan, Shalini Kunapuli, and William McEachen 

Earlier version of this notebook developed by: Seungwoo Sean Son, Keeley Takimoto, Sujude Dalieh

Data Science Modules: http://data.berkeley.edu/education/modules

Some materials are from http://composingprograms.com and https://developers.google.com/edu/python
