---
interact_link: content/psych/03-my-project.ipynb
kernel_name: python3
title: 'My Project'
prev_page:
  url: /psych/02-correlation-regression
  title: 'Correlation, Regression, & Prediction'
next_page:
  url: /rhetoric/rhetoric-intro
  title: 'Rhetoric'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---

# Using your own data

*If you run into errors, check the [common errors](https://docs.google.com/document/d/1-LUvfYYI5UtjYiZerCGIBNgzkaJHNxl4530tgh37uYs/edit?usp=sharing) Google doc first.*

All the information/functions you will need are on the notebooks. The notebooks follow the general order you will want to follow during your own data analysis for the project.

If you need help, please consult the [Data Peers](https://data.berkeley.edu/education/data-science-community)!

# Part 1

## Import the right libraries



{:.input_area}
```python
from datascience import *
import numpy as np
import matplotlib.pyplot as plots
import scipy as sp
%matplotlib inline
import statsmodels.formula.api as smf
plots.style.use('fivethirtyeight')
```


## Read in your `.csv` files

Go back to the file browser (or look below) and choose your first dataset. All are located in the `data` directory.

```
Implicit-Age_IAT.csv               Implicit-Weight_IAT.csv
Implicit-Disability_IAT.csv        Outcome-FBI-Hate-Crimes.csv
Implicit-Race_IAT.csv              Outcome-Heart-Attack-Mortality.csv
Implicit-Religion-Muslim_IAT.csv   Outcome-Neonatal-Deaths.csv
Implicit-Sexuality_IAT.csv         Outcome-Poverty.csv
```

Type its name *exactly* as it appears between the apostrophes below:



{:.input_area}
```python
my_data = Table.read_table('YOUR-FILE-NAME.csv')
my_data
```


Now do the same with your second dataset:



{:.input_area}
```python
my_data2 = Table.read_table('YOUR-FILE-NAME.csv')
my_data2
```


## Wrangle your data

Look back at the previous notebook to figure out how to subset and join your data for analysis:



{:.input_area}
```python
# work on subsetting and joining your data here

my_joined_data = 
```


Now write your merged data to a `.csv`:



{:.input_area}
```python
my_joined_data.to_df().to_csv('my-joined-data.csv')
```


---

# Part 2

## Visualize your data

To find an association between two variables, the `.scatter` method is perhaps the most useful one. 
Try creating a few scatter plots of variables you might think are related among your data!



{:.input_area}
```python
# create some visualizations of your data here


```


## Correlate your data

Calculate a correlation coefficient on your data! Remember: `sp.stats.pearsonr(var1, var2)`



{:.input_area}
```python
# calculate the correlation coefficient here


```


## Regress your data

Run a simple regression on your data



{:.input_area}
```python
# run a regression here


```


Try adding a covariate to that regression below:



{:.input_area}
```python
# run another regression here, this time with a covariate


```


<!--

---

***We would also appreciate if you filled out this feedback form regarding the notebook:
https://goo.gl/forms/ADY9TJU3TGKlllyT2***

***Your input allows us to continue improving our educational notebooks!***

---

-->
