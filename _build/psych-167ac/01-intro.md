---
interact_link: content/psych-167ac/01-intro.ipynb
kernel_name: python3
title: 'Introduction'
prev_page:
  url: /psych-167ac/psych-167ac-intro
  title: 'Psychology'
next_page:
  url: /psych-167ac/02-correlation-regression
  title: 'Correlation & Regression'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---

# Introduction to Importing Data, Using Tables and Creating Graphs

## The Jupyter Notebook

*If you run into errors, check the [common errors](https://docs.google.com/document/d/1-LUvfYYI5UtjYiZerCGIBNgzkaJHNxl4530tgh37uYs/edit?usp=sharing) Google doc first.*

First of all, note that this page is divided into what are called "cells". For example, the following cell is a "code cell" where you will write your code. You'll see a `In [ ]:` next to each cell for code, which is a counter for the cells you have run. You can navigate cells by clicking on them or by using the up and down arrows. Cells will be highlighted as you navigate them.



{:.input_area}
```python
# this is a code cell
```


### Executing cells

<p></p>

<div class="alert alert-info">
You can execute cells with <b><code>Ctrl-Enter</code></b> (which will run the cell and keep the same cell selected), or <b><code>Shift-Enter</code></b> (which will run the cell and then select the next cell).
</div>

Try running the following cell and see what it prints out:



{:.input_area}
```python
print("Hello world!")
```


{:.output .output_stream}
```
Hello world!

```



{:.input_area}
```python
10 + 10
```





{:.output .output_data_text}
```
20
```





{:.input_area}
```python
(10 + 10) / 5
```





{:.output .output_data_text}
```
4.0
```



Now run this cell to `import` some code we'll use today, nothing will `print` out, don't worry!



{:.input_area}
```python
import numpy as np
import matplotlib.pyplot as plt
from datascience import *
%matplotlib inline 
plt.style.use("fivethirtyeight")
```


### Importing

In data analytics, there is almost always a file holding your data that already exists. There are thousands of databases online that contain information on topics from all domains. In general, to import data from a file, we write:

```python
Table.read_table("file_name")
```

Most often, these file names end in `.csv` to show the data format. `.csv` format is popular for spreadsheets and can be imported/exported from programs such as Microsoft Excel, OpenOffice Calc, or Google spreadsheets. 
 
An example is shown below using [U.S. Census data](http://www2.census.gov/programs-surveys/popest/datasets/2010-2015/national/asrh/nc-est2015-agesex-res.csv). 



{:.input_area}
```python
!pwd
```


{:.output .output_stream}
```
/Users/chrispyles/GitHub/modules-textbook/content/psych

```



{:.input_area}
```python
Table.read_table("data/nc-est2015-agesex-res.csv")
```





<div markdown="0" class="output output_html">
<table border="1" class="dataframe">
    <thead>
        <tr>
            <th>SEX</th> <th>AGE</th> <th>CENSUS2010POP</th> <th>ESTIMATESBASE2010</th> <th>POPESTIMATE2010</th> <th>POPESTIMATE2011</th> <th>POPESTIMATE2012</th> <th>POPESTIMATE2013</th> <th>POPESTIMATE2014</th> <th>POPESTIMATE2015</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>0   </td> <td>0   </td> <td>3944153      </td> <td>3944160          </td> <td>3951330        </td> <td>3963087        </td> <td>3926540        </td> <td>3931141        </td> <td>3949775        </td> <td>3978038        </td>
        </tr>
        <tr>
            <td>0   </td> <td>1   </td> <td>3978070      </td> <td>3978090          </td> <td>3957888        </td> <td>3966551        </td> <td>3977939        </td> <td>3942872        </td> <td>3949776        </td> <td>3968564        </td>
        </tr>
        <tr>
            <td>0   </td> <td>2   </td> <td>4096929      </td> <td>4096939          </td> <td>4090862        </td> <td>3971565        </td> <td>3980095        </td> <td>3992720        </td> <td>3959664        </td> <td>3966583        </td>
        </tr>
        <tr>
            <td>0   </td> <td>3   </td> <td>4119040      </td> <td>4119051          </td> <td>4111920        </td> <td>4102470        </td> <td>3983157        </td> <td>3992734        </td> <td>4007079        </td> <td>3974061        </td>
        </tr>
        <tr>
            <td>0   </td> <td>4   </td> <td>4063170      </td> <td>4063186          </td> <td>4077551        </td> <td>4122294        </td> <td>4112849        </td> <td>3994449        </td> <td>4005716        </td> <td>4020035        </td>
        </tr>
        <tr>
            <td>0   </td> <td>5   </td> <td>4056858      </td> <td>4056872          </td> <td>4064653        </td> <td>4087709        </td> <td>4132242        </td> <td>4123626        </td> <td>4006900        </td> <td>4018158        </td>
        </tr>
        <tr>
            <td>0   </td> <td>6   </td> <td>4066381      </td> <td>4066412          </td> <td>4073013        </td> <td>4074993        </td> <td>4097605        </td> <td>4142916        </td> <td>4135930        </td> <td>4019207        </td>
        </tr>
        <tr>
            <td>0   </td> <td>7   </td> <td>4030579      </td> <td>4030594          </td> <td>4043046        </td> <td>4083225        </td> <td>4084913        </td> <td>4108349        </td> <td>4155326        </td> <td>4148360        </td>
        </tr>
        <tr>
            <td>0   </td> <td>8   </td> <td>4046486      </td> <td>4046497          </td> <td>4025604        </td> <td>4053203        </td> <td>4093177        </td> <td>4095711        </td> <td>4120903        </td> <td>4167887        </td>
        </tr>
        <tr>
            <td>0   </td> <td>9   </td> <td>4148353      </td> <td>4148369          </td> <td>4125415        </td> <td>4035710        </td> <td>4063152        </td> <td>4104072        </td> <td>4108349        </td> <td>4133564        </td>
        </tr>
    </tbody>
</table>
<p>... (296 rows omitted)</p>
</div>



That's a lot of information. As you can see from the labels on top, this table shows Biological Sex (0=total, 1=male, 2=female), Age,  2010 Census Information, and predictions for U.S. population for the next five years. 

## Using Tables

We can make criteria to cut down tables. Accessing only the rows, columns, or values specfic to our purpose makes information easier understood. Analysis and conclusions can be made when data is more digestible. 

We need to access the census table above and name it for further use. We assign the table to a variable so that we can reference it later!



{:.input_area}
```python
census_data = Table.read_table("data/nc-est2015-agesex-res.csv")
census_data
```





<div markdown="0" class="output output_html">
<table border="1" class="dataframe">
    <thead>
        <tr>
            <th>SEX</th> <th>AGE</th> <th>CENSUS2010POP</th> <th>ESTIMATESBASE2010</th> <th>POPESTIMATE2010</th> <th>POPESTIMATE2011</th> <th>POPESTIMATE2012</th> <th>POPESTIMATE2013</th> <th>POPESTIMATE2014</th> <th>POPESTIMATE2015</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>0   </td> <td>0   </td> <td>3944153      </td> <td>3944160          </td> <td>3951330        </td> <td>3963087        </td> <td>3926540        </td> <td>3931141        </td> <td>3949775        </td> <td>3978038        </td>
        </tr>
        <tr>
            <td>0   </td> <td>1   </td> <td>3978070      </td> <td>3978090          </td> <td>3957888        </td> <td>3966551        </td> <td>3977939        </td> <td>3942872        </td> <td>3949776        </td> <td>3968564        </td>
        </tr>
        <tr>
            <td>0   </td> <td>2   </td> <td>4096929      </td> <td>4096939          </td> <td>4090862        </td> <td>3971565        </td> <td>3980095        </td> <td>3992720        </td> <td>3959664        </td> <td>3966583        </td>
        </tr>
        <tr>
            <td>0   </td> <td>3   </td> <td>4119040      </td> <td>4119051          </td> <td>4111920        </td> <td>4102470        </td> <td>3983157        </td> <td>3992734        </td> <td>4007079        </td> <td>3974061        </td>
        </tr>
        <tr>
            <td>0   </td> <td>4   </td> <td>4063170      </td> <td>4063186          </td> <td>4077551        </td> <td>4122294        </td> <td>4112849        </td> <td>3994449        </td> <td>4005716        </td> <td>4020035        </td>
        </tr>
        <tr>
            <td>0   </td> <td>5   </td> <td>4056858      </td> <td>4056872          </td> <td>4064653        </td> <td>4087709        </td> <td>4132242        </td> <td>4123626        </td> <td>4006900        </td> <td>4018158        </td>
        </tr>
        <tr>
            <td>0   </td> <td>6   </td> <td>4066381      </td> <td>4066412          </td> <td>4073013        </td> <td>4074993        </td> <td>4097605        </td> <td>4142916        </td> <td>4135930        </td> <td>4019207        </td>
        </tr>
        <tr>
            <td>0   </td> <td>7   </td> <td>4030579      </td> <td>4030594          </td> <td>4043046        </td> <td>4083225        </td> <td>4084913        </td> <td>4108349        </td> <td>4155326        </td> <td>4148360        </td>
        </tr>
        <tr>
            <td>0   </td> <td>8   </td> <td>4046486      </td> <td>4046497          </td> <td>4025604        </td> <td>4053203        </td> <td>4093177        </td> <td>4095711        </td> <td>4120903        </td> <td>4167887        </td>
        </tr>
        <tr>
            <td>0   </td> <td>9   </td> <td>4148353      </td> <td>4148369          </td> <td>4125415        </td> <td>4035710        </td> <td>4063152        </td> <td>4104072        </td> <td>4108349        </td> <td>4133564        </td>
        </tr>
    </tbody>
</table>
<p>... (296 rows omitted)</p>
</div>



This notebook can calculate how large this table is with two functions: num_rows and num_columns. The general form for these functions are table.num_rows and table.num_columns. 

Let's use these on the table above. 



{:.input_area}
```python
census_data.num_rows
```





{:.output .output_data_text}
```
306
```





{:.input_area}
```python
census_data.num_columns
```





{:.output .output_data_text}
```
10
```



That's a 306 x 10 table! We can first start to cut down this table using only some columns. Let's only include biological sex, age and the estimated base for 2010 census data. 

There are two methods to make a table with select columns included. We could either use the 'select' function or the 'drop' function. 

- `select` can create a new table with only the columns indicated in the parameters 
- `drop` can create a new table with columns NOT indicated in the parameters


Here's an example of two equal codes: (keep in mind that we assign each new table to a new variable, to make organization easier). 



{:.input_area}
```python
select_census_data = census_data.select("SEX", "AGE", "ESTIMATESBASE2010")
select_census_data
```





<div markdown="0" class="output output_html">
<table border="1" class="dataframe">
    <thead>
        <tr>
            <th>SEX</th> <th>AGE</th> <th>ESTIMATESBASE2010</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>0   </td> <td>0   </td> <td>3944160          </td>
        </tr>
        <tr>
            <td>0   </td> <td>1   </td> <td>3978090          </td>
        </tr>
        <tr>
            <td>0   </td> <td>2   </td> <td>4096939          </td>
        </tr>
        <tr>
            <td>0   </td> <td>3   </td> <td>4119051          </td>
        </tr>
        <tr>
            <td>0   </td> <td>4   </td> <td>4063186          </td>
        </tr>
        <tr>
            <td>0   </td> <td>5   </td> <td>4056872          </td>
        </tr>
        <tr>
            <td>0   </td> <td>6   </td> <td>4066412          </td>
        </tr>
        <tr>
            <td>0   </td> <td>7   </td> <td>4030594          </td>
        </tr>
        <tr>
            <td>0   </td> <td>8   </td> <td>4046497          </td>
        </tr>
        <tr>
            <td>0   </td> <td>9   </td> <td>4148369          </td>
        </tr>
    </tbody>
</table>
<p>... (296 rows omitted)</p>
</div>





{:.input_area}
```python
drop_census_data = census_data.drop("CENSUS2010POP","POPESTIMATE2010","POPESTIMATE2011","POPESTIMATE2012","POPESTIMATE2013","POPESTIMATE2014","POPESTIMATE2015")
drop_census_data
```





<div markdown="0" class="output output_html">
<table border="1" class="dataframe">
    <thead>
        <tr>
            <th>SEX</th> <th>AGE</th> <th>ESTIMATESBASE2010</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>0   </td> <td>0   </td> <td>3944160          </td>
        </tr>
        <tr>
            <td>0   </td> <td>1   </td> <td>3978090          </td>
        </tr>
        <tr>
            <td>0   </td> <td>2   </td> <td>4096939          </td>
        </tr>
        <tr>
            <td>0   </td> <td>3   </td> <td>4119051          </td>
        </tr>
        <tr>
            <td>0   </td> <td>4   </td> <td>4063186          </td>
        </tr>
        <tr>
            <td>0   </td> <td>5   </td> <td>4056872          </td>
        </tr>
        <tr>
            <td>0   </td> <td>6   </td> <td>4066412          </td>
        </tr>
        <tr>
            <td>0   </td> <td>7   </td> <td>4030594          </td>
        </tr>
        <tr>
            <td>0   </td> <td>8   </td> <td>4046497          </td>
        </tr>
        <tr>
            <td>0   </td> <td>9   </td> <td>4148369          </td>
        </tr>
    </tbody>
</table>
<p>... (296 rows omitted)</p>
</div>



As you can see underneath the table, there are still 296 rows omitted! Our next step is to only include non-gendered data AKA data where SEX=0, neither male or female specific. 

To do this, we need to use a new function `where`. The general form of this function is:

```python
table_name.where(column_name, predicate)
```

To cut our table down to only include `sex=0`, we may use the predicate `are.equal_to()`. Note that we are assigning the new table to a new variable. We are referencing the table stored in an older variable (`select_census_data`), and modifying it. That modification is what is stored in the new variable. 



{:.input_area}
```python
new_census_data = select_census_data.where("SEX", are.equal_to(0))
new_census_data
```





<div markdown="0" class="output output_html">
<table border="1" class="dataframe">
    <thead>
        <tr>
            <th>SEX</th> <th>AGE</th> <th>ESTIMATESBASE2010</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>0   </td> <td>0   </td> <td>3944160          </td>
        </tr>
        <tr>
            <td>0   </td> <td>1   </td> <td>3978090          </td>
        </tr>
        <tr>
            <td>0   </td> <td>2   </td> <td>4096939          </td>
        </tr>
        <tr>
            <td>0   </td> <td>3   </td> <td>4119051          </td>
        </tr>
        <tr>
            <td>0   </td> <td>4   </td> <td>4063186          </td>
        </tr>
        <tr>
            <td>0   </td> <td>5   </td> <td>4056872          </td>
        </tr>
        <tr>
            <td>0   </td> <td>6   </td> <td>4066412          </td>
        </tr>
        <tr>
            <td>0   </td> <td>7   </td> <td>4030594          </td>
        </tr>
        <tr>
            <td>0   </td> <td>8   </td> <td>4046497          </td>
        </tr>
        <tr>
            <td>0   </td> <td>9   </td> <td>4148369          </td>
        </tr>
    </tbody>
</table>
<p>... (92 rows omitted)</p>
</div>



There are still 92 rows omitted! Let's take every 10th entry to cut this table down a little more. 

To do this we need to use the `take` function. The `take` function creates a new table with rows from the original table whose indices(row number) are given. In Python, indices start at 0! 

Here's taking every 10th entry. Inside of the take parentheses is a Python list of numbers from 0 to 90, increasing by 10s. This indicates exactly which rows we want to keep (every 10th row).



{:.input_area}
```python
census_10_year = new_census_data.take([0,10,20,30,40,50,60,70,80,90])
census_10_year
```





<div markdown="0" class="output output_html">
<table border="1" class="dataframe">
    <thead>
        <tr>
            <th>SEX</th> <th>AGE</th> <th>ESTIMATESBASE2010</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>0   </td> <td>0   </td> <td>3944160          </td>
        </tr>
        <tr>
            <td>0   </td> <td>10  </td> <td>4172559          </td>
        </tr>
        <tr>
            <td>0   </td> <td>20  </td> <td>4519556          </td>
        </tr>
        <tr>
            <td>0   </td> <td>30  </td> <td>4285877          </td>
        </tr>
        <tr>
            <td>0   </td> <td>40  </td> <td>4383450          </td>
        </tr>
        <tr>
            <td>0   </td> <td>50  </td> <td>4660457          </td>
        </tr>
        <tr>
            <td>0   </td> <td>60  </td> <td>3621214          </td>
        </tr>
        <tr>
            <td>0   </td> <td>70  </td> <td>2043178          </td>
        </tr>
        <tr>
            <td>0   </td> <td>80  </td> <td>1308608          </td>
        </tr>
        <tr>
            <td>0   </td> <td>90  </td> <td>435695           </td>
        </tr>
    </tbody>
</table>
</div>



Now that sex is all the same, we can drop that column. 



{:.input_area}
```python
final_census_table = census_10_year.drop("SEX")
final_census_table
```





<div markdown="0" class="output output_html">
<table border="1" class="dataframe">
    <thead>
        <tr>
            <th>AGE</th> <th>ESTIMATESBASE2010</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>0   </td> <td>3944160          </td>
        </tr>
        <tr>
            <td>10  </td> <td>4172559          </td>
        </tr>
        <tr>
            <td>20  </td> <td>4519556          </td>
        </tr>
        <tr>
            <td>30  </td> <td>4285877          </td>
        </tr>
        <tr>
            <td>40  </td> <td>4383450          </td>
        </tr>
        <tr>
            <td>50  </td> <td>4660457          </td>
        </tr>
        <tr>
            <td>60  </td> <td>3621214          </td>
        </tr>
        <tr>
            <td>70  </td> <td>2043178          </td>
        </tr>
        <tr>
            <td>80  </td> <td>1308608          </td>
        </tr>
        <tr>
            <td>90  </td> <td>435695           </td>
        </tr>
    </tbody>
</table>
</div>



---

### Tables Essentials!

For your reference, here's a table of useful `Table` functions:

|Name|Example|Purpose|
|-|-|-|
|`Table`|`Table()`|Create an empty table, usually to extend with data|
|`Table.read_table`|`Table.read_table("my_data.csv")`|Create a table from a data file|
|`with_columns`|`tbl = Table().with_columns("N", np.arange(5), "2*N", np.arange(0, 10, 2))`|Create a copy of a table with more columns|
|`column`|`tbl.column("N")`|Create an array containing the elements of a column|
|`sort`|`tbl.sort("N")`|Create a copy of a table sorted by the values in a column|
|`where`|`tbl.where("N", are.above(2))`|Create a copy of a table with only the rows that match some *predicate*|
|`num_rows`|`tbl.num_rows`|Compute the number of rows in a table|
|`num_columns`|`tbl.num_columns`|Compute the number of columns in a table|
|`select`|`tbl.select("N")`|Create a copy of a table with only some of the columns|
|`drop`|`tbl.drop("2*N")`|Create a copy of a table without some of the columns|
|`take`|`tbl.take(np.arange(0, 6, 2))`|Create a copy of the table with only the rows whose indices are in the given array|
|`join`|`tbl1.join("shared_column_name", tbl2)`|Join together two tables with a common column name
|`are.equal_to()`|`tbl.where("SEX", are.equal_to(0))`|find values equal to that indicated|
|`are.not_equal_to()`|`tbl.where("SEX", are.not_equal_to(0))` | find values not including the one indicated|
|`are.above()`| `tbl.where("AGE", are.above(30))` | find values greater to that indicated|
|`are.below()`| `tbl.where("AGE", are.below(40))` | find values less than that indicated |
|`are.between()`| `tbl.where("SEX", are.between(18, 60))` | find values between the two indicated |

---

## Visualizations

Now that we have a manageable table we can start making visualizations! Due to the numerical nature of the census table above, let's first try a scatter plot. 

To create a scatter plot, we need to use the `scatter()` function. The general form is:

```python
table.scatter("column for x axis", "column for y axis")
```

An example is shown below:



{:.input_area}
```python
final_census_table.scatter("AGE", "ESTIMATESBASE2010") 
```



{:.output .output_png}
![png](../images/psych-167ac/01-intro_29_0.png)



With this data, we can also make a line plot. To do this, we need to use the `plot()` function. This works a lot like `scatter()` where the general form is:

```python
table.plot("x column", "y column")
```



{:.input_area}
```python
final_census_table.plot("AGE", "ESTIMATESBASE2010") 
```



{:.output .output_png}
![png](../images/psych-167ac/01-intro_31_0.png)



Though a bar may be better. Bar graphs follow the same formula as scatter plots and line graphs above, with the general form:

```python
table.bar("x axis", "y axis")
```



{:.input_area}
```python
final_census_table.bar("AGE", "ESTIMATESBASE2010") 
```



{:.output .output_png}
![png](../images/psych-167ac/01-intro_33_0.png)



You can also use the functino `barh()` instead of `bar()` in order to flip the bar graph horizontally. Sometimes, this makes for a cleaner visualization.

---

## Merging Tables

We are going to cover one more topic briefly that you will need to use in your project. We are going to look into how to merge two tables that have common information. This technique will be very valuable when the time comes for you to do your own analysis with your own data sets. 

We are going to read in a table with information about psychologists. We will call this new table `psych1`.



{:.input_area}
```python
psych1 = Table.read_table("example-data/psych1.csv")
psych1
```





<div markdown="0" class="output output_html">
<table border="1" class="dataframe">
    <thead>
        <tr>
            <th>Psychologist</th> <th>Birth Year</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Freud       </td> <td>1856      </td>
        </tr>
        <tr>
            <td>Skinner     </td> <td>1904      </td>
        </tr>
        <tr>
            <td>Piaget      </td> <td>1896      </td>
        </tr>
        <tr>
            <td>Maslow      </td> <td>1908      </td>
        </tr>
    </tbody>
</table>
</div>



### Adding rows

You may have another `table` that has the exact same columns and you just want to add the rows to what you already have. Let's read in another short `table` with a couple more psychologists:



{:.input_area}
```python
psych2 = Table.read_table("example-data/psych2.csv")
psych2
```





<div markdown="0" class="output output_html">
<table border="1" class="dataframe">
    <thead>
        <tr>
            <th>Psychologist</th> <th>Birth Year</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Jung        </td> <td>1875      </td>
        </tr>
        <tr>
            <td>Erikson     </td> <td>190       </td>
        </tr>
    </tbody>
</table>
</div>



Great! We see that this second table has the same columns as the first one. Merging these two tables would allow us to consolidate our information. We are going to use the "append" method to append the second table onto the first!



{:.input_area}
```python
psych_merged = Table.copy(psych1)  # copying over the new_psych table to a new variable for the merged table
psych_merged.append(psych2)
psych_merged
```





<div markdown="0" class="output output_html">
<table border="1" class="dataframe">
    <thead>
        <tr>
            <th>Psychologist</th> <th>Birth Year</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Freud       </td> <td>1856      </td>
        </tr>
        <tr>
            <td>Skinner     </td> <td>1904      </td>
        </tr>
        <tr>
            <td>Piaget      </td> <td>1896      </td>
        </tr>
        <tr>
            <td>Maslow      </td> <td>1908      </td>
        </tr>
        <tr>
            <td>Jung        </td> <td>1875      </td>
        </tr>
        <tr>
            <td>Erikson     </td> <td>190       </td>
        </tr>
    </tbody>
</table>
</div>



As you can see, we have succesfully merged these two tables together! Now, let us try merging an additional column onto the original `new_psych` table. 

### Adding columns

Let's pretend that we suddenly have access to the favorite foods of each psychologist. Wow! We definitely want to include that information in our table. This means that we need to merge in a new column to the initial table. Let us print the table first, and then we'll get the other column.



{:.input_area}
```python
psych_merged
```





<div markdown="0" class="output output_html">
<table border="1" class="dataframe">
    <thead>
        <tr>
            <th>Psychologist</th> <th>Birth Year</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Freud       </td> <td>1856      </td>
        </tr>
        <tr>
            <td>Skinner     </td> <td>1904      </td>
        </tr>
        <tr>
            <td>Piaget      </td> <td>1896      </td>
        </tr>
        <tr>
            <td>Maslow      </td> <td>1908      </td>
        </tr>
        <tr>
            <td>Jung        </td> <td>1875      </td>
        </tr>
        <tr>
            <td>Erikson     </td> <td>190       </td>
        </tr>
    </tbody>
</table>
</div>



Now we are going to create to read in our new information.



{:.input_area}
```python
psych_foods = Table.read_table('example-data/favorite_food.csv')
psych_foods
```





<div markdown="0" class="output output_html">
<table border="1" class="dataframe">
    <thead>
        <tr>
            <th>Favorite Food</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Pizza        </td>
        </tr>
        <tr>
            <td>Snickers     </td>
        </tr>
        <tr>
            <td>Grapes       </td>
        </tr>
        <tr>
            <td>Escargot     </td>
        </tr>
        <tr>
            <td>Ice Cream    </td>
        </tr>
        <tr>
            <td>Apples       </td>
        </tr>
    </tbody>
</table>
</div>



Luckily, we are going to assume that each row is in the right order in the column. We are going to use a similar process as before to merge this column! The method we now use is `append_column`. Otherwise, the format stays the same!



{:.input_area}
```python
psych_merged_with_food = Table.copy(psych_merged)  # copying over the new_psych table to a new variable 
psych_merged_with_food.append_column("Favorite Food", psych_foods['Favorite Food'])
psych_merged_with_food
```





<div markdown="0" class="output output_html">
<table border="1" class="dataframe">
    <thead>
        <tr>
            <th>Psychologist</th> <th>Birth Year</th> <th>Favorite Food</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Freud       </td> <td>1856      </td> <td>Pizza        </td>
        </tr>
        <tr>
            <td>Skinner     </td> <td>1904      </td> <td>Snickers     </td>
        </tr>
        <tr>
            <td>Piaget      </td> <td>1896      </td> <td>Grapes       </td>
        </tr>
        <tr>
            <td>Maslow      </td> <td>1908      </td> <td>Escargot     </td>
        </tr>
        <tr>
            <td>Jung        </td> <td>1875      </td> <td>Ice Cream    </td>
        </tr>
        <tr>
            <td>Erikson     </td> <td>190       </td> <td>Apples       </td>
        </tr>
    </tbody>
</table>
</div>



As you can see, we've successfully merged a column to our table too!

### Joining on columns

Suppose now that you have more information on the these psycologists (another column), but the rows aren't in the right order so you can't just `append_column`. Luckily, you have their names. 



{:.input_area}
```python
psych_birthplaces = Table.read_table("example-data/birthplaces.csv")
psych_birthplaces
```





<div markdown="0" class="output output_html">
<table border="1" class="dataframe">
    <thead>
        <tr>
            <th>Psychologist</th> <th>Birth Place</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Maslow      </td> <td>New York      </td>
        </tr>
        <tr>
            <td>Erikson     </td> <td>Germany       </td>
        </tr>
        <tr>
            <td>Skinner     </td> <td>Pennsylvania  </td>
        </tr>
        <tr>
            <td>Piaget      </td> <td>Switzerland   </td>
        </tr>
        <tr>
            <td>Freud       </td> <td>Czech Republic</td>
        </tr>
        <tr>
            <td>Jung        </td> <td>Switzerland   </td>
        </tr>
    </tbody>
</table>
</div>



Awesome! We love more data, but how can I merge this back into our existing information? We can't just add a column because the order is different.

***Solution***: We can use the `join` method and tell it which column the two tables have in common, and it will match the data to the correct row:



{:.input_area}
```python
final_table = psych_merged_with_food.join("Psychologist", psych_birthplaces)
final_table
```





<div markdown="0" class="output output_html">
<table border="1" class="dataframe">
    <thead>
        <tr>
            <th>Psychologist</th> <th>Birth Year</th> <th>Favorite Food</th> <th>Birth Place</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Erikson     </td> <td>190       </td> <td>Apples       </td> <td>Germany       </td>
        </tr>
        <tr>
            <td>Freud       </td> <td>1856      </td> <td>Pizza        </td> <td>Czech Republic</td>
        </tr>
        <tr>
            <td>Jung        </td> <td>1875      </td> <td>Ice Cream    </td> <td>Switzerland   </td>
        </tr>
        <tr>
            <td>Maslow      </td> <td>1908      </td> <td>Escargot     </td> <td>New York      </td>
        </tr>
        <tr>
            <td>Piaget      </td> <td>1896      </td> <td>Grapes       </td> <td>Switzerland   </td>
        </tr>
        <tr>
            <td>Skinner     </td> <td>1904      </td> <td>Snickers     </td> <td>Pennsylvania  </td>
        </tr>
    </tbody>
</table>
</div>



That's super cool!

---

## SUMMARY

### You've learned a lot in this module! Let's look back on the key parts.

- To import data from a .csv/.txt file, we write `Table.read_table("file_name")`.

- To create our own table, we write `Table( ).with_columns("Column Name", array_name, . . .)` . 

- To count number of rows, we use `table_name.num_rows`.

- To count number of columns, we use `table_name.num_columns`.

- To create a new table with only the columns indicated in the parameters, we use `table_name.select("COLUMN NAME", ...)`. 

- To create a new table without the columns indicated in the parameters, we use `table_name.drop("COLUMN NAME", ...)`. 

- To create a table with only certain values, we can use `table_name.where(column_name, predicate)`.

- To create a new table with indicated rows from the original table, we use `table_name.take([index 1, index 2, . . . ])`. Remember in Python indices start at 0!

- To create a scatter plot, we use `table.scatter(column for x axis, column for y axis)`.

- To create a line plot, we use `table.plot(x column, y column)`.

- To make a bar graphs, we can use either `table.bar(x column, y column)` or `table.barh(x column, y column)`. 

- To make a histogram, we use `table.hist(x axis, bins(optional), unit(optional))`. 

- To merge tables, we use either `append` or `append_column`.

- To merge two tables with a common column name we use the `join` method.

---

With just some simple code, we were able to do an incredible amount of data analysis! Play around with the examples until you feel comfortable with the content of this notebook. We will be using notebooks to analyze your own data sets in the future! Please ask if you have questions!


If you need help, please consult the [Data Peers](https://data.berkeley.edu/education/data-science-community)!
