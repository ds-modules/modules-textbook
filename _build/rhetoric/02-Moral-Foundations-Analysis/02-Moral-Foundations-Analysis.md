---
redirect_from:
  - "/rhetoric/02-moral-foundations-analysis/02-moral-foundations-analysis"
interact_link: content/rhetoric/02-Moral-Foundations-Analysis/02-Moral-Foundations-Analysis.ipynb
kernel_name: python3
title: 'Moral Foundations Analysis'
prev_page:
  url: /rhetoric/01-intro/01-intro
  title: 'Introduction'
next_page:
  url: 
  title: ''
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---

#  Data Analysis: Moral Foundations Theory
---
<img src="https://c1.staticflickr.com/7/6240/6261650491_0cd6c701bb_b.jpg" style="width: 500px; height: 275px;" />

### Professor Amy Tick

Moral Foundations Theory (MFT) hypothesizes that people's sensitivity to the foundations is different based on their political ideology: liberals are more sensitive to care and fairness, while conservatives are equally sensitive to all five. Here, we'll explore whether we can find evidence for MFT in the campaign speeches of 2016 United States presidential candidates. For our main analysis, we'll go through the data science process start to finish to recreate a simplified version of the analysis done by Jesse Graham, Jonathan Haidt, and Brian A. Nosek in their 2009 paper ["Liberals and Conservatives Rely on Different Sets of Moral Foundations"](http://projectimplicit.net/nosek/papers/GHN2009.pdf). Finally, we'll explore other ways to visualize and use this data in rhetorical analysis.

*Estimated Time: 50 minutes*

---

### Topics Covered
- Word count using a dictionary
- Data visualization with pandas
- Graph interpretations

### Table of Contents


1 - [Data Set and Test Statistic](#section 1)<br>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1.1 - [2016 Campaign Speeches](#subsection 1)<br>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 1.2 - [Moral Foundations Dictionary](#subsection 2) <br>

2 - [Data Analysis](#section 2)<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 2.1 - [Calculating Perceptages](#subsection 3)<br>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 2.2 - [Filtering Table Rows](#subsection 4)<br>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 2.3 - [Democrats](#subsection 5) <br>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 2.4 - [Republicans](#subsection 6) <br>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 2.5 - [Democrats vs Republicans](#subsection 7) <br>

3 - [Additional Visualizations](#section 3)<br>

4 - [Assignment: Run Analysis with Your Dictionary](#section 4)<br>

**Dependencies:**



{:.input_area}
```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
%matplotlib inline
import json
from nltk.stem.snowball import SnowballStemmer
import os
import re
```


---
## Intro: The Data Science Process

Module 01 defined data science as an interdisciplinary field, combining statistics, computer science, and domain expertise to understand the world and solve problems. The data science process can be thought of like this:

<img src="https://upload.wikimedia.org/wikipedia/commons/b/ba/Data_visualization_process_v1.png" style="width: 550px; height: 400px;" />

This module walks through a simplified version of the process to explore speech data and probe Moral Foundations Theory. Steps done in this module are in bold.

1. Raw Data Collection: speech data is collected into csv files via web-scraping.
2. **Data Processing/Cleaning**: speech data is transformed to enable analysis. Some processing/cleaning has already been done.
3. **Exploratory Data Analysis**: transform, visualize, and summarize data with the goal of understanding the data set, finding possible issues, and looking for potential questions to explore further.
4. **Models and Algorithms**: develop and test a *model*- a theory of how the data was generated (in this case, Moral Foundations Theory).
5. Communicate, Visualize, Report: to be discussed in Module 03.

---
## Part 1: Speech Data and Foundations Dictionary  <a id='section 1'></a>

In Part 1, we'll get familiar with our data set and determine a way to answer questions using the data.

### 2016 Campaign Speeches <a id='subsection 1'></a>

Run the cell below to load the data.




{:.input_area}
```python
# load the data from csv files into a table. 
speeches = pd.read_csv('campaign_2016.csv', index_col=0)

# show the first 5 rows of the table
speeches.head()
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
      <td>Jeb Bush</td>
      <td>R</td>
      <td>c</td>
      <td>June 15, 2015</td>
      <td>Remarks Announcing Candidacy for President at ...</td>
      <td>Thank you all very much. I always feel welcome...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Jeb Bush</td>
      <td>R</td>
      <td>c</td>
      <td>July 30, 2015</td>
      <td>Remarks to the National Urban League Conferenc...</td>
      <td>Thank you all very much. I appreciate your hos...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Jeb Bush</td>
      <td>R</td>
      <td>c</td>
      <td>August 11, 2015</td>
      <td>Remarks at the Ronald Reagan Presidential Libr...</td>
      <td>Thank you very much. It's good to be with all ...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Jeb Bush</td>
      <td>R</td>
      <td>c</td>
      <td>September 9, 2015</td>
      <td>Remarks in Garner, North Carolina</td>
      <td>Thank you very much. I appreciate your hospita...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Jeb Bush</td>
      <td>R</td>
      <td>c</td>
      <td>November 2, 2015</td>
      <td>Remarks in Tampa, Florida</td>
      <td>Thank you. It's great to be in Tampa with so m...</td>
    </tr>
  </tbody>
</table>
</div>
</div>



Take a moment to look at this table. Before doing any analysis, it's important to understand:
* the size of the table (how much data does it contain?)
* the structure of the table (how is the data organized?)
* what information it contains (what are the aspects of each record described in columns? what does each record (row) represent?)




{:.input_area}
```python
# use this cell to expore the speeches DataFrame
# the `shape` attribute is useful to get the number of rows and columns
speeches.shape
```





{:.output .output_data_text}
```
(430, 6)
```



### Moral Foundations Dictionary <a id='subsection 2'></a>

In ["Liberals and Conservatives Rely on Different Sets of Moral Foundations"](http://projectimplicit.net/nosek/papers/GHN2009.pdf), one of the methods Graham, Haidt, and Nosek use to measure people's use of Moral Foundations Theory is to count how often they use words related to each foundation. This will be our test statistic for today. To calculate it, we'll need a dictionary of words related to each moral foundation. 

The dictionary we'll use today comes from a database called [WordNet](https://wordnet.princeton.edu), in which "nouns, verbs, adjectives and adverbs are grouped into sets of cognitive synonyms (synsets), each expressing a distinct concept." By querying WordNet for semantically related words, it was possible to build a dictionary automatically using a Python program.

Run the cell below to load the dictionary and assign it to the variable 'mft_dict'.



{:.input_area}
```python
# Load a dictionary into the mft_dict variable
# The path is the argument for the open function. It gives the location of the dictionary file.
# To use the Wordnet dictionary from the Module 02 lecture, set the path to '../mft_data/foundations_dict.json'
# To use your hand-coded dictionary, set the path to '../mft_data/my_dict.json'
with open('../mft_data/foundations_dict.json') as json_data:
    mft_dict = json.load(json_data)

# Stem the words in your dictionary (this will help you get more matches)
stemmer = SnowballStemmer('english')

for foundation in mft_dict.keys():
    curr_words = mft_dict[foundation]
    stemmed_words = [stemmer.stem(word) for word in curr_words]
    mft_dict[foundation] = stemmed_words
```


We can see the keys of the dictionary using the .keys() function:



{:.input_area}
```python
keys = mft_dict.keys()
list(keys)
```





{:.output .output_data_text}
```
['authority/subversion',
 'care/harm',
 'fairness/cheating',
 'liberty/oppression',
 'loyalty/betrayal',
 'sanctity/degradation']
```



And we can look up the entries associated with a key by putting the key in brackets:



{:.input_area}
```python
mft_dict
```





{:.output .output_data_text}
```
{'authority/subversion': ['respect',
  'esteem',
  'regard',
  'subver',
  'say-so',
  'offic',
  'disrespect',
  'valu',
  'obedi',
  'assur',
  'honor',
  'disesteem',
  'agenc',
  'corrupt',
  'honour',
  'domin',
  'author',
  'observ',
  'confid',
  'defer',
  'bureau',
  'authori',
  'sure',
  'sanction'],
 'care/harm': ['hurt',
  'scath',
  'precaut',
  'concern',
  'attent',
  'damag',
  'care',
  'manag',
  'impair',
  'worri',
  'harm',
  'trauma',
  'guardianship',
  'aid',
  'tend',
  'caution',
  'forethought',
  'tutelag',
  'injuri',
  'upkeep',
  'mainten',
  'charg'],
 'fairness/cheating': ['equiti',
  'fair',
  'cuckold',
  'unsportsmanlik',
  'screw',
  'dirti',
  'candour',
  'cheat',
  'proport',
  'balanc',
  'inequ',
  'chican',
  'betray',
  'candor',
  'adult',
  'chous',
  'unsport',
  'unfair',
  'two-tim',
  'foul',
  'shaft',
  'fair-mind'],
 'liberty/oppression': ['self-direct',
  'self-suffici',
  'autonomi',
  'conquest',
  'burdensom',
  'independ',
  'subjug',
  'oner',
  'oppress',
  'subject',
  'self-r',
  'liberti',
  'conquer',
  'heavi'],
 'loyalty/betrayal': ['traitor',
  'disloyalti',
  'treason',
  'betray',
  'commit',
  'dedic',
  'commit',
  'consign',
  'perfidi',
  'truth',
  'subver',
  'allegi',
  'trueness',
  'veriti',
  'inscript',
  'treacheri',
  'fealti',
  'loyalti',
  'committ',
  'falsiti'],
 'sanctity/degradation': ['pure',
  'guilt',
  'respect',
  'impur',
  'reward',
  'disrespect',
  'deba',
  'honor',
  'sanctitud',
  'white',
  'sanctiti',
  'honour',
  'holi',
  'degrad',
  'adult',
  'dross',
  'observ',
  'innoc',
  'natur',
  'ingenu',
  'aba',
  'dishonor',
  'puriti',
  'abject',
  'unholi',
  'sinless',
  'humili']}
```



Try looking up the entries for the other keys by filling in for '...' in the cell below.



{:.input_area}
```python
# look up a key in mft_dict
...
```


There's something odd about some of the entries: they're not words! The entries in this dictionary have been **stemmed**, meaning they have been reduced to their smallest meaningful root. 

We can see why this is helpful with an example. Python can count the number of times a string can be found in another string using the string method 'count':



{:.input_area}
```python
# Counts the number of times the second string appears in the first string
"Data science is the best major, says data scientist.".count('science')
```





{:.output .output_data_text}
```
1
```



It returns one match, for the second word. But, 'scientist' is very closely related to 'science', and many times we will want to match them both. A stem allows Python to find all words with a common root. Try running the count again with a stem that matches both 'science' and 'scientist'.



{:.input_area}
```python
# Fill in the parenthesis with a stem that will match both 'science' and 'scientist'
"Data science is the best major, says data scientist.".count('...')
```





{:.output .output_data_text}
```
0
```



Another thing you might have noticed is that all the entries in our dictionary are lowercase. This could be a problem when we do our text analysis. Try counting the number of times 'rhetoric' appears in the example sentence.



{:.input_area}
```python
# Fill in the parenthesis to count how often 'rhetoric' appears in the sentence
"Rhetoric major says back: NEVER argue with a rhetoric student.".count('...')
```





{:.output .output_data_text}
```
0
```



We can clearly see the word 'rhetoric' appears twice, but the count function only returns 1. That's because Python differentiates between capital and lowercase letters:



{:.input_area}
```python
'r' is 'R'
```





{:.output .output_data_text}
```
False
```



To get around this, we can use the .lower() function, which changes all letters in the string to lowercase:



{:.input_area}
```python
"Rhetoric major says back: NEVER argue with a rhetoric student.".lower()
```





{:.output .output_data_text}
```
'rhetoric major says back: never argue with a rhetoric student.'
```



Let's add a column to our 'speeches' table that contains the lowercase text of the speeches. The `clean_text` function lowers the case of the text in addition to implementing some of the text cleaning methods seen in Module 01, like removing the punctuation and splitting the text into individual words.



{:.input_area}
```python
def clean_text(text):
    # remove punctuation using a regular expression (not covered in these modules)
    p = re.compile(r'[^\w\s]')
    no_punc = p.sub(' ', text)
    # convert to lowercase
    no_punc_lower = no_punc.lower()
    # split into individual words
    clean = no_punc_lower.split()
    return clean
    
speeches['clean_speech'] = [clean_text(s) for s in speeches['Speech']]

speeches.head()
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
      <th>clean_speech</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Jeb Bush</td>
      <td>R</td>
      <td>c</td>
      <td>June 15, 2015</td>
      <td>Remarks Announcing Candidacy for President at ...</td>
      <td>Thank you all very much. I always feel welcome...</td>
      <td>[thank, you, all, very, much, i, always, feel,...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Jeb Bush</td>
      <td>R</td>
      <td>c</td>
      <td>July 30, 2015</td>
      <td>Remarks to the National Urban League Conferenc...</td>
      <td>Thank you all very much. I appreciate your hos...</td>
      <td>[thank, you, all, very, much, i, appreciate, y...</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Jeb Bush</td>
      <td>R</td>
      <td>c</td>
      <td>August 11, 2015</td>
      <td>Remarks at the Ronald Reagan Presidential Libr...</td>
      <td>Thank you very much. It's good to be with all ...</td>
      <td>[thank, you, very, much, it, s, good, to, be, ...</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Jeb Bush</td>
      <td>R</td>
      <td>c</td>
      <td>September 9, 2015</td>
      <td>Remarks in Garner, North Carolina</td>
      <td>Thank you very much. I appreciate your hospita...</td>
      <td>[thank, you, very, much, i, appreciate, your, ...</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Jeb Bush</td>
      <td>R</td>
      <td>c</td>
      <td>November 2, 2015</td>
      <td>Remarks in Tampa, Florida</td>
      <td>Thank you. It's great to be in Tampa with so m...</td>
      <td>[thank, you, it, s, great, to, be, in, tampa, ...</td>
    </tr>
  </tbody>
</table>
</div>
</div>



---
## Part 2: Exploratory Data Analysis <a id='section 2'></a>

Now that we have our speech data and our dictionary, we can start our exploratory analysis. The exploratory analysis in this module will be more focused than in most cases since we already have a model in mind- Moral Foundations Theory.

To get a sense of how Moral Foundations words were used in campaign speeches, we'll do three things:
1. Count the occurances of words from our dictionary in each speech
2. Calculate how often words from each category are used by each political party
3. Plot the percents on a bar graph

Think about what you know about Moral Foundations Theory. If this data is consistent with the theory, what should our analysis show for Republican candidates? What about for Democratic candidates? Try sketching a possible graph for each political party, assuming that candidates' speech aligns with the theory.

### Calculating Percentages <a id='subsection 3'></a>

We're interesting in knowing the percent of words that correspond to a Moral Foundation in speeches- in other words, how often candidates use words related to a specific foundation. 

(Bonus question: why don't we just use the **number** of Moral Foundation words instead of the **percent** as our test statistic?)

To calculate the percent, we'll first need the total number of words in each speech.



{:.input_area}
```python
# create a new column called 'total_words'
speeches['total_words'] = [len(speech) for speech in speeches['clean_speech']]
speeches.head()
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
      <th>clean_speech</th>
      <th>total_words</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Jeb Bush</td>
      <td>R</td>
      <td>c</td>
      <td>June 15, 2015</td>
      <td>Remarks Announcing Candidacy for President at ...</td>
      <td>Thank you all very much. I always feel welcome...</td>
      <td>[thank, you, all, very, much, i, always, feel,...</td>
      <td>2284</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Jeb Bush</td>
      <td>R</td>
      <td>c</td>
      <td>July 30, 2015</td>
      <td>Remarks to the National Urban League Conferenc...</td>
      <td>Thank you all very much. I appreciate your hos...</td>
      <td>[thank, you, all, very, much, i, appreciate, y...</td>
      <td>2638</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Jeb Bush</td>
      <td>R</td>
      <td>c</td>
      <td>August 11, 2015</td>
      <td>Remarks at the Ronald Reagan Presidential Libr...</td>
      <td>Thank you very much. It's good to be with all ...</td>
      <td>[thank, you, very, much, it, s, good, to, be, ...</td>
      <td>3735</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Jeb Bush</td>
      <td>R</td>
      <td>c</td>
      <td>September 9, 2015</td>
      <td>Remarks in Garner, North Carolina</td>
      <td>Thank you very much. I appreciate your hospita...</td>
      <td>[thank, you, very, much, i, appreciate, your, ...</td>
      <td>1880</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Jeb Bush</td>
      <td>R</td>
      <td>c</td>
      <td>November 2, 2015</td>
      <td>Remarks in Tampa, Florida</td>
      <td>Thank you. It's great to be in Tampa with so m...</td>
      <td>[thank, you, it, s, great, to, be, in, tampa, ...</td>
      <td>2550</td>
    </tr>
  </tbody>
</table>
</div>
</div>



Next, we need to calculate the number of matches to entries in our dictionary for each foundation for each speech. 

Run the next cell to add six new columns to `speeches`, one per foundation, that show the number of word matches.



{:.input_area}
```python
#Note: much of the following code is not covered in these modules. Read the comments to get a sense of what it does.

# do the following code for each foundation
for foundation in mft_dict.keys():
    # create a new, empty column
    num_match_words = np.zeros(len(speeches))
    stems = mft_dict[foundation]
    
    # do the following code for each foundation word
    for stem in stems:
        # find synonym matches
        wd_count = np.array([sum([wd.startswith(stem) for wd in speech]) for speech in speeches['clean_speech']])
        # add the number of matches to the total
        num_match_words += wd_count
        
    # create a new column for each foundation with the number of foundation words per speech
    speeches[foundation] = num_match_words

speeches.head()
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
      <th>clean_speech</th>
      <th>total_words</th>
      <th>authority/subversion</th>
      <th>care/harm</th>
      <th>fairness/cheating</th>
      <th>liberty/oppression</th>
      <th>loyalty/betrayal</th>
      <th>sanctity/degradation</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Jeb Bush</td>
      <td>R</td>
      <td>c</td>
      <td>June 15, 2015</td>
      <td>Remarks Announcing Candidacy for President at ...</td>
      <td>Thank you all very much. I always feel welcome...</td>
      <td>[thank, you, all, very, much, i, always, feel,...</td>
      <td>2284</td>
      <td>4.0</td>
      <td>4.0</td>
      <td>3.0</td>
      <td>0.0</td>
      <td>7.0</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Jeb Bush</td>
      <td>R</td>
      <td>c</td>
      <td>July 30, 2015</td>
      <td>Remarks to the National Urban League Conferenc...</td>
      <td>Thank you all very much. I appreciate your hos...</td>
      <td>[thank, you, all, very, much, i, appreciate, y...</td>
      <td>2638</td>
      <td>8.0</td>
      <td>2.0</td>
      <td>7.0</td>
      <td>0.0</td>
      <td>4.0</td>
      <td>9.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Jeb Bush</td>
      <td>R</td>
      <td>c</td>
      <td>August 11, 2015</td>
      <td>Remarks at the Ronald Reagan Presidential Libr...</td>
      <td>Thank you very much. It's good to be with all ...</td>
      <td>[thank, you, very, much, it, s, good, to, be, ...</td>
      <td>3735</td>
      <td>12.0</td>
      <td>5.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>4.0</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Jeb Bush</td>
      <td>R</td>
      <td>c</td>
      <td>September 9, 2015</td>
      <td>Remarks in Garner, North Carolina</td>
      <td>Thank you very much. I appreciate your hospita...</td>
      <td>[thank, you, very, much, i, appreciate, your, ...</td>
      <td>1880</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>1.0</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Jeb Bush</td>
      <td>R</td>
      <td>c</td>
      <td>November 2, 2015</td>
      <td>Remarks in Tampa, Florida</td>
      <td>Thank you. It's great to be in Tampa with so m...</td>
      <td>[thank, you, it, s, great, to, be, in, tampa, ...</td>
      <td>2550</td>
      <td>8.0</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>1.0</td>
      <td>0.0</td>
      <td>7.0</td>
    </tr>
  </tbody>
</table>
</div>
</div>



To calculate the percentage of foundation words per speech, divide the number of matched words by the number of total words and multiply by 100.



{:.input_area}
```python
for foundation in mft_dict.keys():
    speeches[foundation] = (speeches[foundation] / speeches['total_words']) * 100

speeches.head()
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
      <th>clean_speech</th>
      <th>total_words</th>
      <th>authority/subversion</th>
      <th>care/harm</th>
      <th>fairness/cheating</th>
      <th>liberty/oppression</th>
      <th>loyalty/betrayal</th>
      <th>sanctity/degradation</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Jeb Bush</td>
      <td>R</td>
      <td>c</td>
      <td>June 15, 2015</td>
      <td>Remarks Announcing Candidacy for President at ...</td>
      <td>Thank you all very much. I always feel welcome...</td>
      <td>[thank, you, all, very, much, i, always, feel,...</td>
      <td>2284</td>
      <td>0.175131</td>
      <td>0.175131</td>
      <td>0.131349</td>
      <td>0.000000</td>
      <td>0.306480</td>
      <td>0.175131</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Jeb Bush</td>
      <td>R</td>
      <td>c</td>
      <td>July 30, 2015</td>
      <td>Remarks to the National Urban League Conferenc...</td>
      <td>Thank you all very much. I appreciate your hos...</td>
      <td>[thank, you, all, very, much, i, appreciate, y...</td>
      <td>2638</td>
      <td>0.303260</td>
      <td>0.075815</td>
      <td>0.265353</td>
      <td>0.000000</td>
      <td>0.151630</td>
      <td>0.341168</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Jeb Bush</td>
      <td>R</td>
      <td>c</td>
      <td>August 11, 2015</td>
      <td>Remarks at the Ronald Reagan Presidential Libr...</td>
      <td>Thank you very much. It's good to be with all ...</td>
      <td>[thank, you, very, much, it, s, good, to, be, ...</td>
      <td>3735</td>
      <td>0.321285</td>
      <td>0.133869</td>
      <td>0.026774</td>
      <td>0.000000</td>
      <td>0.107095</td>
      <td>0.133869</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Jeb Bush</td>
      <td>R</td>
      <td>c</td>
      <td>September 9, 2015</td>
      <td>Remarks in Garner, North Carolina</td>
      <td>Thank you very much. I appreciate your hospita...</td>
      <td>[thank, you, very, much, i, appreciate, your, ...</td>
      <td>1880</td>
      <td>0.159574</td>
      <td>0.053191</td>
      <td>0.053191</td>
      <td>0.000000</td>
      <td>0.053191</td>
      <td>0.212766</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Jeb Bush</td>
      <td>R</td>
      <td>c</td>
      <td>November 2, 2015</td>
      <td>Remarks in Tampa, Florida</td>
      <td>Thank you. It's great to be in Tampa with so m...</td>
      <td>[thank, you, it, s, great, to, be, in, tampa, ...</td>
      <td>2550</td>
      <td>0.313725</td>
      <td>0.117647</td>
      <td>0.039216</td>
      <td>0.039216</td>
      <td>0.000000</td>
      <td>0.274510</td>
    </tr>
  </tbody>
</table>
</div>
</div>



### Filtering table rows <a id='subsection 4'></a>

To examine the data for a particular political party, it is necessary to filter out rows of our table that correspond to speeches from the other party, something we can do with **Boolean indexing**.

A **Boolean** is a Python data type. There are exactly two: `True` and `False`. A Boolean expression is an expression that evaluates to `True` or `False`. Boolean expressions are often conditions on two variables; that is, they ask how one variable compares to another (e.g. is `a` greater than `b`? Does `a` equal `c`?).



{:.input_area}
```python
# These are all Booleans
True

not False

6 > 0

"Ted Cruz" == "zodiac killer"
```





{:.output .output_data_text}
```
False
```



Note that Python uses `==` to check if two things are equal. This is because the `=` sign is already used for variable assignement.

Filtering out DataFrame rows can be broken into three steps:
1. identify the correct feature column 
2. specify the desired condition for that column
3. index the Dataframe with that condition in square brackets

Here's an example of how to create a new table with only Bernie Sanders' speeches.



{:.input_area}
```python
# find the column
speech_col = speeches['Candidate']

# specify the condition
sanders_condition =  speech_col == 'Bernie Sanders'

# index the original DataFrame by the condition
sanders_speeches = speeches[sanders_condition]
sanders_speeches.head()
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
      <th>clean_speech</th>
      <th>total_words</th>
      <th>authority/subversion</th>
      <th>care/harm</th>
      <th>fairness/cheating</th>
      <th>liberty/oppression</th>
      <th>loyalty/betrayal</th>
      <th>sanctity/degradation</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>5877</th>
      <td>Bernie Sanders</td>
      <td>D</td>
      <td>c</td>
      <td>April 30, 2015</td>
      <td>Interview with Ed Schultz of MSNBC Regarding S...</td>
      <td>Schultz: A gentleman who has appeared on the p...</td>
      <td>[schultz, a, gentleman, who, has, appeared, on...</td>
      <td>3645</td>
      <td>0.329218</td>
      <td>0.082305</td>
      <td>0.054870</td>
      <td>0.027435</td>
      <td>0.109739</td>
      <td>0.109739</td>
    </tr>
    <tr>
      <th>5878</th>
      <td>Bernie Sanders</td>
      <td>D</td>
      <td>c</td>
      <td>April 30, 2015</td>
      <td>Interview with Wolf Blitzer of CNN Regarding S...</td>
      <td>Blitzer: I want to move to politics right now ...</td>
      <td>[blitzer, i, want, to, move, to, politics, rig...</td>
      <td>1764</td>
      <td>0.566893</td>
      <td>0.000000</td>
      <td>0.056689</td>
      <td>0.170068</td>
      <td>0.000000</td>
      <td>0.453515</td>
    </tr>
    <tr>
      <th>5879</th>
      <td>Bernie Sanders</td>
      <td>D</td>
      <td>c</td>
      <td>April 30, 2015</td>
      <td>Interview with Andrea Mitchell of MSNBC Regard...</td>
      <td>Sanders (from video clip): I believe that in a...</td>
      <td>[sanders, from, video, clip, i, believe, that,...</td>
      <td>976</td>
      <td>0.204918</td>
      <td>0.409836</td>
      <td>0.204918</td>
      <td>0.614754</td>
      <td>0.000000</td>
      <td>0.204918</td>
    </tr>
    <tr>
      <th>5880</th>
      <td>Bernie Sanders</td>
      <td>D</td>
      <td>c</td>
      <td>May 6, 2015</td>
      <td>Interview with Chris Cuomo of CNN's "New Day"</td>
      <td>CUOMO: Senator Sanders, welcome to the race. G...</td>
      <td>[cuomo, senator, sanders, welcome, to, the, ra...</td>
      <td>1561</td>
      <td>0.128123</td>
      <td>0.000000</td>
      <td>0.192184</td>
      <td>0.000000</td>
      <td>0.064061</td>
      <td>0.064061</td>
    </tr>
    <tr>
      <th>5881</th>
      <td>Bernie Sanders</td>
      <td>D</td>
      <td>c</td>
      <td>May 11, 2015</td>
      <td>Interview with Andrea Mitchell of MSNBC</td>
      <td>MITCHELL: Vermont Senator and Democratic presi...</td>
      <td>[mitchell, vermont, senator, and, democratic, ...</td>
      <td>910</td>
      <td>0.219780</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.109890</td>
      <td>0.000000</td>
      <td>0.219780</td>
    </tr>
  </tbody>
</table>
</div>
</div>



### Democrats <a id='subsection 5'></a>

Let's start by looking at Democratic candidates. First, we need to make a table that only contains Democrats using boolean indexing.



{:.input_area}
```python
# Filter out non-Democrat speeches
party_col = speeches['Party']

dem_cond = party_col == 'D'

democrats = speeches[dem_cond]

democrats.head()
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
      <th>clean_speech</th>
      <th>total_words</th>
      <th>authority/subversion</th>
      <th>care/harm</th>
      <th>fairness/cheating</th>
      <th>liberty/oppression</th>
      <th>loyalty/betrayal</th>
      <th>sanctity/degradation</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>436</th>
      <td>Lincoln Chafee</td>
      <td>D</td>
      <td>c</td>
      <td>June 3, 2015</td>
      <td>Remarks Announcing Candidacy for President at ...</td>
      <td>Thank you, Bob. Thank you, Bob and Mark, very ...</td>
      <td>[thank, you, bob, thank, you, bob, and, mark, ...</td>
      <td>5512</td>
      <td>0.235849</td>
      <td>0.181422</td>
      <td>0.090711</td>
      <td>0.036284</td>
      <td>0.145138</td>
      <td>0.108853</td>
    </tr>
    <tr>
      <th>437</th>
      <td>Lincoln Chafee</td>
      <td>D</td>
      <td>c</td>
      <td>July 17, 2015</td>
      <td>Remarks at the Iowa Democrats Hall of Fame Din...</td>
      <td>Congratulations to the Hall of Fame Inductees....</td>
      <td>[congratulations, to, the, hall, of, fame, ind...</td>
      <td>745</td>
      <td>0.268456</td>
      <td>0.134228</td>
      <td>0.268456</td>
      <td>0.000000</td>
      <td>0.805369</td>
      <td>0.268456</td>
    </tr>
    <tr>
      <th>438</th>
      <td>Lincoln Chafee</td>
      <td>D</td>
      <td>c</td>
      <td>October 23, 2015</td>
      <td>Remarks Announcing the End of Presidential Cam...</td>
      <td>Once again it is a pleasure to join so many De...</td>
      <td>[once, again, it, is, a, pleasure, to, join, s...</td>
      <td>939</td>
      <td>0.212993</td>
      <td>0.212993</td>
      <td>0.000000</td>
      <td>0.106496</td>
      <td>0.425985</td>
      <td>0.106496</td>
    </tr>
    <tr>
      <th>570</th>
      <td>Hillary Clinton</td>
      <td>D</td>
      <td>c</td>
      <td>January 20, 2007</td>
      <td>Video Transcript: Presidential Exploratory Com...</td>
      <td>HILLARY CLINTON: I announced today that I am f...</td>
      <td>[hillary, clinton, i, announced, today, that, ...</td>
      <td>349</td>
      <td>0.286533</td>
      <td>0.573066</td>
      <td>0.000000</td>
      <td>0.286533</td>
      <td>1.719198</td>
      <td>0.286533</td>
    </tr>
    <tr>
      <th>571</th>
      <td>Hillary Clinton</td>
      <td>D</td>
      <td>c</td>
      <td>January 22, 2007</td>
      <td>Remarks in a "Let the Conversation Begin Webcast"</td>
      <td>SENATOR CLINTON: Hi, everyone, and welcome to ...</td>
      <td>[senator, clinton, hi, everyone, and, welcome,...</td>
      <td>5349</td>
      <td>0.355207</td>
      <td>0.261731</td>
      <td>0.037390</td>
      <td>0.018695</td>
      <td>0.149561</td>
      <td>0.093475</td>
    </tr>
  </tbody>
</table>
</div>
</div>



We have our percentages for the Democratic party, but it's much easier to understand what's going on when the results are in graph form. Let's start by looking at the average percents for Democrats as a group. 




{:.input_area}
```python
# select the foundations columns and calculate the mean percent for each
avg_dem_stats = (democrats.loc[:, list(mft_dict.keys())]
                 .apply(np.mean)
                 .to_frame('D_percent'))

avg_dem_stats
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
      <th>D_percent</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>authority/subversion</th>
      <td>0.321495</td>
    </tr>
    <tr>
      <th>care/harm</th>
      <td>0.292418</td>
    </tr>
    <tr>
      <th>fairness/cheating</th>
      <td>0.082472</td>
    </tr>
    <tr>
      <th>liberty/oppression</th>
      <td>0.030215</td>
    </tr>
    <tr>
      <th>loyalty/betrayal</th>
      <td>0.145686</td>
    </tr>
    <tr>
      <th>sanctity/degradation</th>
      <td>0.204513</td>
    </tr>
  </tbody>
</table>
</div>
</div>



Now, create a horizontal bar plot by calling the `.plot.barh()` method on `avg_dem_stats`. 



{:.input_area}
```python
avg_dem_stats.plot.barh()
```





{:.output .output_data_text}
```
<matplotlib.axes._subplots.AxesSubplot at 0x1271e9860>
```




{:.output .output_png}
![png](../../images/rhetoric/02-Moral-Foundations-Analysis/02-Moral-Foundations-Analysis_52_1.png)



Take a look at this graph. What does it show? How does it compare with the predictions of MFT?


### Republicans <a id='subsection 6'></a>

Now, let's repeat the process for Republicans. Replace the ellipses with the correct code to select only Republican speeches, then run the cell to create the table. 

(Hint: look back at how we made the 'democrats' table to see how to fill in the ellipses)



{:.input_area}
```python
# Filter out non-Republican speeches

# select 'Party' column from 'speeches'
party_col = speeches['Party']

# create a condition (boolean expression) that checks if a party is Republican
republican_cond = party_col == 'R'

# index `speeches` using `republican_cond`
republicans = speeches[republican_cond]

# uncomment the next line to show the first 5 rows of the `republican` DataFrame
republicans.head()
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
      <th>clean_speech</th>
      <th>total_words</th>
      <th>authority/subversion</th>
      <th>care/harm</th>
      <th>fairness/cheating</th>
      <th>liberty/oppression</th>
      <th>loyalty/betrayal</th>
      <th>sanctity/degradation</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Jeb Bush</td>
      <td>R</td>
      <td>c</td>
      <td>June 15, 2015</td>
      <td>Remarks Announcing Candidacy for President at ...</td>
      <td>Thank you all very much. I always feel welcome...</td>
      <td>[thank, you, all, very, much, i, always, feel,...</td>
      <td>2284</td>
      <td>0.175131</td>
      <td>0.175131</td>
      <td>0.131349</td>
      <td>0.000000</td>
      <td>0.306480</td>
      <td>0.175131</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Jeb Bush</td>
      <td>R</td>
      <td>c</td>
      <td>July 30, 2015</td>
      <td>Remarks to the National Urban League Conferenc...</td>
      <td>Thank you all very much. I appreciate your hos...</td>
      <td>[thank, you, all, very, much, i, appreciate, y...</td>
      <td>2638</td>
      <td>0.303260</td>
      <td>0.075815</td>
      <td>0.265353</td>
      <td>0.000000</td>
      <td>0.151630</td>
      <td>0.341168</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Jeb Bush</td>
      <td>R</td>
      <td>c</td>
      <td>August 11, 2015</td>
      <td>Remarks at the Ronald Reagan Presidential Libr...</td>
      <td>Thank you very much. It's good to be with all ...</td>
      <td>[thank, you, very, much, it, s, good, to, be, ...</td>
      <td>3735</td>
      <td>0.321285</td>
      <td>0.133869</td>
      <td>0.026774</td>
      <td>0.000000</td>
      <td>0.107095</td>
      <td>0.133869</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Jeb Bush</td>
      <td>R</td>
      <td>c</td>
      <td>September 9, 2015</td>
      <td>Remarks in Garner, North Carolina</td>
      <td>Thank you very much. I appreciate your hospita...</td>
      <td>[thank, you, very, much, i, appreciate, your, ...</td>
      <td>1880</td>
      <td>0.159574</td>
      <td>0.053191</td>
      <td>0.053191</td>
      <td>0.000000</td>
      <td>0.053191</td>
      <td>0.212766</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Jeb Bush</td>
      <td>R</td>
      <td>c</td>
      <td>November 2, 2015</td>
      <td>Remarks in Tampa, Florida</td>
      <td>Thank you. It's great to be in Tampa with so m...</td>
      <td>[thank, you, it, s, great, to, be, in, tampa, ...</td>
      <td>2550</td>
      <td>0.313725</td>
      <td>0.117647</td>
      <td>0.039216</td>
      <td>0.039216</td>
      <td>0.000000</td>
      <td>0.274510</td>
    </tr>
  </tbody>
</table>
</div>
</div>



Then, calculate the averages.



{:.input_area}
```python
# select the foundations columns and calculate the mean percent for each
avg_rep_stats = (republicans.loc[:, list(mft_dict.keys())]
                 .apply(np.mean)
                 .to_frame('R_percent'))

avg_rep_stats 
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
      <th>R_percent</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>authority/subversion</th>
      <td>0.393636</td>
    </tr>
    <tr>
      <th>care/harm</th>
      <td>0.176955</td>
    </tr>
    <tr>
      <th>fairness/cheating</th>
      <td>0.066454</td>
    </tr>
    <tr>
      <th>liberty/oppression</th>
      <td>0.039025</td>
    </tr>
    <tr>
      <th>loyalty/betrayal</th>
      <td>0.080041</td>
    </tr>
    <tr>
      <th>sanctity/degradation</th>
      <td>0.191499</td>
    </tr>
  </tbody>
</table>
</div>
</div>



Finally, create a bar plot of `avg_rep_stats` using the `.plot.barh()` method.



{:.input_area}
```python
# your code here
avg_rep_stats.plot.barh()
```





{:.output .output_data_text}
```
<matplotlib.axes._subplots.AxesSubplot at 0x12cd937b8>
```




{:.output .output_png}
![png](../../images/rhetoric/02-Moral-Foundations-Analysis/02-Moral-Foundations-Analysis_60_1.png)



How does this plot compare with Moral Foundations Theory predictions?

### Democrats vs Republicans <a id='subsection 7'></a>

Comparing two groups becomes much easier when they are plotted on the same graph. 

First, combine `avg_dem_stats` and `avg_rep_stats` into one DataFrame with the `join` function. `join` is called on one table using `.join()`, takes the other table as its argument (in the parentheses), and returns a table with the indices matched. 

Here's an example of a simple join:



{:.input_area}
```python
peanut_butter = pd.DataFrame(data=[2.99, 3.49], index = ['Trader Joes', 'Safeway'], columns=['pb_price'])
peanut_butter
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
      <th>pb_price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Trader Joes</th>
      <td>2.99</td>
    </tr>
    <tr>
      <th>Safeway</th>
      <td>3.49</td>
    </tr>
  </tbody>
</table>
</div>
</div>





{:.input_area}
```python
jelly = pd.DataFrame(data=[4.99, 3.59], index = ['Trader Joes', 'Safeway'], columns=['jelly_price'])
jelly
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
      <th>jelly_price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Trader Joes</th>
      <td>4.99</td>
    </tr>
    <tr>
      <th>Safeway</th>
      <td>3.59</td>
    </tr>
  </tbody>
</table>
</div>
</div>





{:.input_area}
```python
jelly.join(peanut_butter)
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
      <th>jelly_price</th>
      <th>pb_price</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Trader Joes</th>
      <td>4.99</td>
      <td>2.99</td>
    </tr>
    <tr>
      <th>Safeway</th>
      <td>3.59</td>
      <td>3.49</td>
    </tr>
  </tbody>
</table>
</div>
</div>



Now, write the code to join `avg_dem_stats` with `avg_rep_stats`.



{:.input_area}
```python
# fill in the ellipses with your code
all_avg_stats = avg_dem_stats.join(avg_rep_stats)
all_avg_stats
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
      <th>D_percent</th>
      <th>R_percent</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>authority/subversion</th>
      <td>0.321495</td>
      <td>0.393636</td>
    </tr>
    <tr>
      <th>care/harm</th>
      <td>0.292418</td>
      <td>0.176955</td>
    </tr>
    <tr>
      <th>fairness/cheating</th>
      <td>0.082472</td>
      <td>0.066454</td>
    </tr>
    <tr>
      <th>liberty/oppression</th>
      <td>0.030215</td>
      <td>0.039025</td>
    </tr>
    <tr>
      <th>loyalty/betrayal</th>
      <td>0.145686</td>
      <td>0.080041</td>
    </tr>
    <tr>
      <th>sanctity/degradation</th>
      <td>0.204513</td>
      <td>0.191499</td>
    </tr>
  </tbody>
</table>
</div>
</div>



Then, make a horizontal bar plot for `all_avg_stats'.



{:.input_area}
```python
# your code here
all_avg_stats.plot.barh()
```





{:.output .output_data_text}
```
<matplotlib.axes._subplots.AxesSubplot at 0x11325f3c8>
```




{:.output .output_png}
![png](../../images/rhetoric/02-Moral-Foundations-Analysis/02-Moral-Foundations-Analysis_70_1.png)




It can be hard to make comparison judgments if the bar lengsth are very similar. The next cell creates a plot of only the difference in average foundation word usage of Democrats and Republicans. A positive value means Democrats use the word more frequently; a negative value indicates Republicans use it more frequently.



{:.input_area}
```python
# uncomment the next two lines to plot the difference in percent of foundations words per speech by party
party_diffs = pd.DataFrame(data = avg_dem_stats['D_percent'] - avg_rep_stats['R_percent'],
                          columns = ["dem_rep_pct_diff"], 
                          index = mft_dict.keys())
party_diffs.plot.bar()
```





{:.output .output_data_text}
```
<matplotlib.axes._subplots.AxesSubplot at 0x12eebbac8>
```




{:.output .output_png}
![png](../../images/rhetoric/02-Moral-Foundations-Analysis/02-Moral-Foundations-Analysis_72_1.png)



---
## Part 3: Additional Visualizations<a id='section 3'></a>

Many different graphs can be generated from the same data set to facilitate different comparisons. For example, we can compare the average use of foundation words by individual Democrats...



{:.input_area}
```python
dem_indivs = (democrats.loc[:, list(mft_dict.keys()) + ['Candidate']]
             .groupby('Candidate')
             .mean())

dem_indivs.plot.barh(figsize=(8, 8))
```





{:.output .output_data_text}
```
<matplotlib.axes._subplots.AxesSubplot at 0x107d55ac8>
```




{:.output .output_png}
![png](../../images/rhetoric/02-Moral-Foundations-Analysis/02-Moral-Foundations-Analysis_75_1.png)



...or individual Republicans.



{:.input_area}
```python
rep_indivs = (republicans.loc[:, list(mft_dict.keys()) + ['Candidate']]
             .groupby('Candidate')
             .mean())

rep_indivs.plot.barh(figsize=(8, 20))
```





{:.output .output_data_text}
```
<matplotlib.axes._subplots.AxesSubplot at 0x12f041cf8>
```




{:.output .output_png}
![png](../../images/rhetoric/02-Moral-Foundations-Analysis/02-Moral-Foundations-Analysis_77_1.png)



We can also examine how a candidate uses foundation words over time. The following plot shows foundation word usage for Donald Trump in the weeks leading up to the election.



{:.input_area}
```python
# select Trump's speeches and drop unnecessary columns
trump = (republicans[republicans['Candidate'] == "Donald Trump"]
         .loc[:, list(mft_dict.keys()) + ['Date']])

# set the speech dates as the table index
trump['Date'] = pd.to_datetime(trump['Date'])
trump = (trump.set_index('Date')
         .loc['2016-07-01':])

# plot the data
trump.plot(figsize = (10, 6))
```





{:.output .output_data_text}
```
<matplotlib.axes._subplots.AxesSubplot at 0x12f716f60>
```




{:.output .output_png}
![png](../../images/rhetoric/02-Moral-Foundations-Analysis/02-Moral-Foundations-Analysis_79_1.png)



What other kinds of plots could be generated from this data? What other questions might we be able to explore with these or other plots?

---
## Part 4: Run Analysis with Your Dictionary <a id='section 4'></a>

One of the advantages of coding is how easy it is to repeat one method of analysis with different parameters. For instance, changing a single line of code means that all of the word counts, proportions, and graphs in the above sections can be recalculated using a different dictionary of Moral Foundations words.

To change what dictionary is loaded to the `mft_dict` variable, go to [Part 1.2: Moral Foundations Dictionary](#subsection 2) <br> and follow the instructions in the first code cell. 

Once the dictionary load code has been changed, the easiest way to regenerate all the tables, percents, and graphs is to go to the `Cell` menu and click `Run all`. This ensures that all the statistics used to make the graphs will be recalculated with the new dictionary.

For this assignment, answer the following three questions about the graphs made using **your hand-coded dictionary**:

1. What does each graph show?
2. How are these graphs different from the ones made using the Wordnet dictionary?
3. Do these graphs support Moral Foundations Theory?

---

## Bibliography

* Election documents scraped from http://www.presidency.ucsb.edu/2016_election.php
* Graham, J., Haidt, J., & Nosek, B. A. (2009). Liberals and conservatives rely on different sets of moral foundations. Journal of personality and social psychology, 96(5), 1029. http://projectimplicit.net/nosek/papers/GHN2009.pdf, October 9 2017.

---
Notebook developed by: Keeley Takimoto, Sean Seungwoo Son, Sujude Dalieh

Data Science Modules: http://data.berkeley.edu/education/modules

