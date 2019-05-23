---
interact_link: content/econ/problem-sets.ipynb
kernel_name: python3
title: 'Problem Sets Overview'
prev_page:
  url: /econ/convergence-to-balanced-growth-path
  title: 'Convergence to Balanced Growth Path'
next_page:
  url: /econ/ps1/PS1
  title: 'Problem Set 1'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---

# Econ 101B Problem Sets

## Setting Up the Environment



{:.input_area}
```python
%matplotlib inline
import numpy as np
import matplotlib as mpl
import matplotlib.pyplot as plt
import seaborn as sns
from pandas import DataFrame, Series
from datetime import datetime
import pandas as pd
import plotly
plotly.tools.set_credentials_file(username='', api_key='')
import plotly.plotly as py
import plotly.graph_objs as go
from plotly.graph_objs import Scatter
sns.set(color_codes = True)
import statsmodels.formula.api as smf
```


## Chapter 1: Introduction to Macroeconomics

#### Suppose a quantity grows at a steady proportional rate of 3% per year. How long will it take to double? Quadruple? Grow 1024-fold?

#### Suppose we have a quantity x(t) that varies over time following the equation: $\frac{dx(t)}{dt} = -(0.06)x + 0.36$.

Without integrating the equation

1. Tell me what the long-run steady-state value of $x$--that is, the limit of $x$ as $t$ approaches in infinity--is going to be.
2. Suppose that the value of $x$ at time $t=0$, $x(0)$, equals 12. Once again, without integrating the equation, tell me how long it will take $x$ to close half the distance between its initial value of 12 and its steady-state value. 
3. How long will it take to close 3/4 of the distance? 
4. 7/8 of the distance? 
5. 15/16 of the distance?

Now you are allowed to integrate $\frac{dx(t)}{dt} = -(0.06)x + 0.36$.

1. Write down and solve the indefinite integral.
2. Write down and solve the definite integral for the initial condition $x(0) = 12$. 
3. Write down and solve the definite integral for the initial condition $x(0)=6$.

#### Suppose we have a quantity $z = \left ( \frac{x}{y} \right ) ^\beta$

Suppose x is growing at 4% per year and that $\beta=\frac{1}{4}$:

1. How fast is $z$ growing if $y$ is growing at 0% per year? 
2. If $y$ is growing at 2% per year? 
3. If $y$ is growing at 4% per year?

#### Rule of 72

1. If a quantity grows at about 3% per year, how long will it take to double?
2. If a quantity shrinks at about 4% per year, how long will it take it to halve itself?
3. If a quantity doubles five times, how large is it relative to its original value?
4. If a quantity halves itself three times, how large is it relative to its original value?

#### Why do DeLong and Olney think that the interest rate and the level of the stock market are important macroeconomic variables?

#### What are the principal flaws in using national product per worker as a measure of material welfare? Given these flaws, why do we use it anyway?

#### What is the difference between the nominal interest rate and the real interest rate? Why do DeLong and Olney think that the real interest rate is more important?

## Chapter 2: Measuring the Macroeconomy

#### National Income and Product Accounting

Explain whether or not, why, and how the following items are included in the calculations of national product:

1. Increases in business inventories. 
2. Fees earned by real estate agents on selling existing homes. 
3. Social Security checks written by the government. 
4. Building of a new dam by the Army Corps of Engineers. 
5. Interest that your parents pay on the mortgage they have on their house. 
6. Purchases of foreign-made trucks by American residents

#### In or Out of National Product? And Why

Explain whether or not, why, and how the following items are included in the calculation of national product:

1. The sale for \\$25,000 of an automobile that cost \\$20,000 to manufacture that had been produced here at home last year and carried over in inventory.
2. The sale for \\$35,000 of an automobile that cost \\$25,000 to manufacture newly- made at home this year.
3. The sale for \\$45,000 of an automobile that cost \\$30,000 to manufacture that was newly-made abroad this year and imported.
4. The sale for \\$25,000 of an automobile that cost \\$20,000 to manufacture that was made abroad and imported last year.

#### In or Out of National Product? And Why II

Explain whether or not, why, and how the following items are included in the calculation of GDP:

1. The purchase for \\$500 of a dishwasher produced here at home this year.
2. The purchase for \\$500 of a dishwasher made abroad this year.
3. The purchase for \\$500 of a used dishwasher.
4. The manufacture of a new dishwasher here at home for \\$500 of a dishwasher that
then nobody wants to buy.

#### Components of National Income and Product

Suppose that the appliance store buys a refrigerator from the manufacturer on December 15, 2018 for \\$600, and that you then buy that refrigerator on January 15, 2019 for \\$1000:

1. What is the contribution to GDP in 2018? 
2. How is the refrigerator accounted for in the NIPA in 2019? 
3. What is the contribution to GDP in 2018? 
4. How is the refrigerator accounted for in the NIPA in 2019?

#### Estimating National Product

The Bureau of Economic Analysis measures national product in two different ways: as total expenditure on the economy’s output of goods and services and as the total income of everyone in the economy. Since – as you learned in earlier courses – these two things are the same, the two approaches should give the same answer. But in practice they do not.

For the period 2006:Q4–2012:Q4, get quarterly data on real GDP measured on the expenditure side (referred to in the National Income and Product Accounts as “Real Gross Domestic Product, chained dollars” – these are the headline GDP numbers you will see discussed in the news) and real GDP measured on the income side (referred to as “Real
Gross Domestic Income, chained dollars”).

1. Describe where you found the data.
2. Compute the growth rate at an annual rate of each of the two series by quarter for
2007:Q1–2012:Q4.
3. Describe any two things you see when you compare the two series that you find
interesting, and explain why you find them interesting.

#### Calculating Real Magnitudes:

1. When you calculate real national product, do you do so by dividing nominal national product by the price level or by subtracting the price level from nominal national product? 
2. When you calculate the real interest rate, do you do so by dividing the nominal interest rate by the price level or by subtracting the inflation rate from the nominal interest rate? 
3. Are your answers to (a) and (b) the same? Why or why not?

#### What, roughly, was the highest level the U.S. unemployment rate reached in:

1. the 20th century? 
2. the past fifty years? 
3. the twenty years before 2006?
4. Given your answers to (1) through (3), Do you think there is a connection between your answer to the qeustion above and the fact that Federal Reserve Chair Alan Greenspan received a five-minute standing ovation at the end of the first of many events marking his retirement in 2005?

#### The State of the Labor Market

1. About how many people lose or quit their jobs in an average month?
2. About how many people get jobs in an average month?
3. About how many people are unemployed in an average month?
4. About how many people are at work in an average month?
5. About how many people are unemployed now?

#### National Income Accounting:

1. What was the level of real GDP in 2005 dollars in 1970?
2. What was the rate of inflation in the United States in 2000?
3. Explain whether or not, how, and why the following items are included in the calculation of GDP: (i) rent you pay on an apartment, (ii) purchase of a used textbook, (iii) purchase of a new tank by the Department of Defense, (iv) watching an advertisement on youtube.

## Chapter 3: Thinking Like an Economist

#### In what sense can a line on a graph "be" an equation?

## Chapter 4: Theories of Economic Growth

#### Production Functions

1. Suppose α = 1/2, E=1, L=100, and K=64; what is output per worker Y/L?
2. Suppose α = 1/2, E=3, L=196, and K=49; what is output per worker Y/L?
3. If both capital K and labor L triple, what happens to total output Y?
3. Holding E=1, suppose that capital per worker increases from 4 to 8 and then from 8 to 12. What happens to output per worker?

#### Budget Deficits

Consider an economy in which the depreciation rate is 2% per year, the rate of population increase is 1% per year, the rate of technological progress is 1% per year, and the private savings rate is 17% of GDP. Suppose that the government increases its budget deficit--which had been at 1% of GDP for a long time--to 5% of GDP and keeps it there indefinitely.

1. What is the effect of this shift on the economy's steady-state capital-output ratio? b. What is the effect of this shift on the economy's steady state growth path for output per worker?
2. Suppose that your forecast of output per worker 20 years in the future had been \\$120,000. What is your new forecast of output per worker twenty years hence?
3. Suppose that environmental regulations lead to a diversion of investment spending from investments that boost the capital stock to investments that replace polluting with less-polluting capital. In our standard growth model, what would be the consequences of such a diversion for the economy's capital-output ratio and for its balanced-growth path? Would it make sense to say that these environmental regulations diminished the economy's wealth?

#### Savings Rates

Consider an economy in which the depreciation rate is 4% per year, the rate of population increase is 1% per year, the rate of technological progress is 2% per year, and the national savings rate is 21% of GDP. Suppose that thrift-promoting policies raise the savings rate to 24.5% of GDP and keep it there indefinitely.

1. Calculate—that is write an equation for it as a function of time—what the level of output per worker would have been had the savings rate remained at 21%, and had the economy initially been on its steady-state growth path.
2. Calculate—that is write an equation for it as a function of time—what the level of output per worker will have be now that the savings rate has increased.

#### Population Growth

Many project that by the middle of the twenty-first century the population of the United States will be stable. Using the Solow growth model, what would the qualitative effects of such a downward shift in the growth rate of the labor force be on the growth of output per worker and to the growth of total output? (Consider both the effect of zero population growth on the steady-state growth path, and the transition from the "old" positive population growth to the "new" zero population growth steady-state growth path.)

#### Long Run Models

We have cautioned you that the Solow growth model is—especially in its focus-on- the-steady-state-growth-path version—a long run model. What do we mean by that?

#### Doubling Capital per Worker

Consider an economy with the production function: $Y=K^\alpha(EL)^{1−\alpha}$ on its steady-state balanced-growth path:

1. Suppose α = 1/2, E=1, L=100, and K=64; what is output per worker Y/L?
2. Suppose α = 1/2, E=3, L=196, and K=49; what is output per worker Y/L?
3. If both capital K and labor L triple, what happens to total output Y?
4. Holding E=1, suppose that capital per worker increases from 4 to 8 and then from
8 to 12. What happens to output per worker?

#### Walking Up the Production Function

Consider an economy with the production function: $Y=K^\alpha(EL)^{1−\alpha}$ on its steady-state balanced-growth path:

1. Suppose α = 1/3, E=1, L=100, and K=64; what is output per worker Y/L?
2. Suppose α = 1/3, E=3, L=196, and K=49; what is output per worker Y/L?
3. If both capital K and labor L double, what happens to total output Y?
4. Holding E=1, suppose that capital per worker increases from 1 to 4 and then from
4 to 9. What happens to output per worker?

#### Balanced Growth Path

Suppose that an economy's production function is $Y=K^{0.5}(EL)^{0.5}$; suppose further that the savings rate s is 40  percent of GDP, that the depreciation rate δ is 4 percent per year, the population growth rate n is 0, and the rate of growth g of the efficiency of the labor force is 2 percent per year.

1. What is the steady-state balanced-growth capital-output ratio?
2. How fast does output per worker grow along the steady-state balanced-growth
path?
3. How fast does total output grow along the steady-state balanced-growth path?
4. Suppose that all variables are the same save the production function, which instead is: $K^{0.8}(EL)^{0.2}$; how would your answers be different? Why would your answers are different?

## Chapter 5: Reality of Economic Growth: History

#### Escape from the Malthusian Trap

Suppose somebody who hasn't taken any economics courses were to ask you why humanity escaped from the Malthusian trap--of very low standards of living and slow population growth rates that nevertheless put pressure on available natural resources and kept output per worker from rising--in which humanity found itself between the year 8000 B.C.E. and 1800. What answer would you give? (One paragraph only, please!)

#### Malthusian Economy

Suppose—in the Malthusian model with natural resources—that population growth depends on the level of output per worker, so that:

$$n = 2.00002 \left ( \frac{Y}{L} - \\$400 \right ) $$

That is, the population and labor force growth rate $n$ is zero if output per worker equals \\$400, and that each \\$100 increase in output per worker raises the population growth rate by 0.2 percent per year. Suppose also that the natural-resources parameter β in the production function: $Y = K^\alpha (EL)^{1 - \alpha - \beta} (ER)^\beta$ is 0.2. Suppose also that $gL=0$.

1. If $gR=0.2\%$ per year, what is the steady-state rate of population growth? If it is 0.4% per year? 1% per year?
2. How long does it take the population to double for each of the efficiency-of-using- resources growth rates above?
3. By what multiple does the population grow in a millennium for each of the efficiency-of-labor growth rates in (a) above?

#### Malthus

Write a paragraph explaining to somebody who hasn’t taken this course how human populations could increase from 170 million in year 1 to 500 million in year 1500 without there being any noticeable increases in life expectancy or median material standards of living.

#### Economic History Facts

1. Roughly, how much larger was global world product in 1800 than it was in the year 1?
2. Roughly, how large is global world product today?
3. Roughly, how much larger is global world product today than it was in 2000?

#### Argentina

In 1960, Argentina had a level of output per worker of $14,000/year. In the 1940s and 1950s it had had a savings-investment share of 24% and a labor-force growth rate of 2% per year. Since 1960 Argentina has averaged a savings-investment share of 15% and a labor force growth rate of 1%/year. Assume that Argentina in the 1940s and 1950s had an efficiency of labor growth rate g of 1%/year. Assume α= 2⁄3. Assume the depreciation rate δ is 5%/year. Assume that Argentina in 1960 was on its 1940s and 1950s steady-state balanced-growth path, and that Argentina today is on its post-1960 balanced growth path.

1. What was Argentinaʼs capital-output ratio in 1960?
2. What was Argentinaʼs efficiency of labor E in 1960?
3. If the efficiency-of-labor growth rate had been 1%/year since 1960, what would Argentinaʼs efficiency of labor, capital-output ratio, and level of output per worker be today?
4. If the efficiency of labor growth rate had been 2%/year since 1960, what would Argentinaʼs efficiency of labor, capital-output ratio, and level of output per worker be today?
5. If the efficiency of labor growth rate had been 3%/year since 1960, what would Argentinaʼs efficiency of labor, capital-output ratio, and level of output per worker be today?
6. If the efficiency of labor growth rate had been 4%/year since 1960, what would Argentinaʼs efficiency of labor, capital-output ratio, and level of output per worker be today?
7. If the efficiency of labor growth rate had been 5%/year since 1960, what would Argentinaʼs efficiency of labor, capital-output ratio, and level of output per worker be today?
8. Argentinaʼs level of output per worker today is $27000/year. What do you guess its growth rate of the efficiency of labor has been on average since 1960?

## Chapter 6: Reality of Economic Growth: Present and Future

#### Suppose somebody

who hasn't taken any economics courses were to ask you why it is that some countries are so very, very much poorer than others in the world today. What answer would you give? (Two paragraphs only, please!)

#### Constant Returns

Suppose we have our standard growth model with s =15 percent, n = 1 percent, g = 1 percent, and δ = 3 percent. Suppose also that the current level of the efficiency of labor E is \\$5,000 per year and the current level of capital per worker is \\$25,000. Suppose further that the parameter α in the production function is equal to 1: α = 1.

1. What can you say about output per worker in this economy? What would you project output per worker to be at some point in the distant future?
2. Suppose the savings rate s is not 15 percent but 17.5 percent. How would that change your projections of the future growth of output per worker?
3. What effect does growth in the efficiency of labor have on output per worker when α = 1?
4. Why aren’t the normal Solow model tools of analysis and rules of thumb much use when α = 1?

#### Computer Revolution

Today it appears that because of the computer revolution the rate of growth of the efficiency of labor in the United States has more than doubled, from 1.0 percent per year before 1995 to about 3.0 percent per year since. Suppose this increase were to be permanent.Suppose the rate of labor force growth were to remain constant at 1 percent per year, the depreciation rate were to remain constant at 3 percent per year, and the American savings rate (plus foreign capital invested in America) were to remain constant at 20 percent per year. Assume that the efficiency of labor in the U.S. in 2006 is $18,500 per year, and that the diminishing-returns-to-capital parameter α is 1/2.

1. What is the change in the steady-state capital-output ratio because of this acceleration in efficiency-of-labor growth? What is the new steady-state capital- output ratio?
2. How would such a permanent acceleration in the rate of growth of the efficiency of labor change your forecast of the level of output per worker in 2040?
3. How would your answers to (a) and (b) be different if α were 1/3? If it were 2/3?

#### Capital:

Suppose that you misestimate the capital stock—think that its rate of growth is lower than it actually is—but otherwise understand the parameters and the growth rates of the base-camp Solow growth model. How will your conclusions about the sources of economic growth be off?

#### Prices of Capital Goods

Let us suppose that the price of capital goods in terms of output-in-general P(k) varies, so that the law of motion for the capital stock in the Solow growth model is not:

$$\frac{dK}{dt} = sY − δK$$

but is instead:

$$dKt = \frac{sY}{P(k)} − δK$$

1. Derive the steady-state balanced-growth capital-output ratio (K/Y)* for this model in which the price of capital goods varies.
2. Suppose that richer countries have lower prices of capital goods according to: Y−η PK =L Using your answer from (5), suppose that η=1/3. Now consider the three cases of α equal to 0.25, 0.5, and 0.75. Suppose that something happens in the economy to permanently increase the savings rate from 20% to 21%. 
3. By what proportional fraction does steady-state output-per-worker increase relative to its previous steady-state balanced-growth path?

#### Leninism and Stalinism

Take a look at http://en.wikipedia.org/wiki/List_of_countries_by_GDP_%28PPP%29_per_capita_per_hour — the wikipedia page for “List of countries by GDP (PPP) per capita per hour.” Select some countries that were once ruled by Communist governments and compare them to neighboring countries that were lucky enough to escape Communist rule. How big a shadow do you guess having a Communist government imposes on a nation on average, even today?

#### Long-Run American Growth

Take a look at the 2006 Economic Report of the President at http://www.gpoaccess.gov/eop/index.html. Read pages 36-37 and 43-46. How would you translate the arguments made by Eddie Lazear and his colleagues about the long-run growth rate of the American economy into concepts introduced in this course?

#### International Disparities

1. Roughly, what is the gap between real per capita GDP in the U.S. today and real per capita GDP in China?
2. Roughly, what is the gap between real per capita GDP in China today and real per
capita GDP in Mozambique?

#### Botswana

In the 1950s Botswanaʼs savings rate averaged 6 percent of GDP. In 1960 Botswanaʼs level of GDP per capita was 900 of todayʼs dollars per year. Since 1960 Botswanaʼs savings rate has averaged 30 percent of GDP. Today Botswanaʼs level of GDP per capita is 15000 per year. 

Assume that the diminishing-returns parameter α in our production function for Botswana is 0.5, that Botswanaʼs population growth rate n has been constant at 2 percent per year, and that its depreciation rate δ has been constant at 4 percent per year. Assume that Botswana was back in 1960 on its old steady- state balanced-growth path (for an s=0.06) and is now on its new steady-state balanced-growth path (for an s=0.30)

1. Suppose there had been no growth in the efficiency of labor in Botswana between 1960 and 2011, what do you predict that the level of GDP per capita would be in Botswana today?
2. How fast has the efficiency of labor grown in Botswana over the past 50 years?
3. What was the value of the efficiency of labor in Botswana in 1960?
4. What is the value of the efficiency of labor in Botswana today?

#### Zambia

In the 1950s Zambiaʼs savings rate averaged 24.5 percent of GDP. In 1960 Zambiaʼs level of GDP per capita was 1800 of todayʼs dollars per year. Since 1980 Zambiaʼs savings rate has averaged 24.5 percent of GDP. Today Zambiaʼs level of GDP per capita is 1300 per year. 

Assume that the diminishing-returns parameter α in our production function for Zambia is 0.5, that Zambiaʼs population growth rate n has been constant at 3% per year, and that its depreciation rate δ has been constant at 4.64% per year. Assume that Zambiaʼs was back in 1960 on its old steady-state balanced-growth path (for an s=0.3) and is now on its new steady-state balanced- growth path (for an s=0.2)

1. Suppose there had been no growth in the efficiency of labor in Zambia between 1960 and 2011, what do you predict that the level of GDP per capita would be in Zambia today?
2. How fast has the efficiency of labor grown in Zambia over the past 50 years?
3. What was the value of the efficiency of labor in Zambia in 1960?
4. What is the value of the efficiency of labor in Zambia today?

#### France

Since 1946 French population growth (including illegal immigration) has been constant at about 1 percent per year and France has had a savings share of 25 percent of GDP. Today France has a GDP per capita level of about 35,000 per year. The rate of growth of the efficiency of labor in France since the end of World War II in France has been constant at about 2 percent per year. Assume that France is today on its steady-state balanced-growth path.

1. If France remains on its current steady-state balanced-growth path, what will GDP per capita be in France in 2050?
2. If France remains on its current steady-state balanced-growth path, what will GDP per capita be in France in 2100?
3. What would Franceʼs level of GDP per capita have been back in 1946 if it had then been on todayʼs steady-state balanced-growth path?
4. In fact, Franceʼs level of GDP per capita back in 1946 was about 3,000 per year even though its efficiency of labor has grown at 2 percent per year since the end of World War II. Why do you think its level back then was so low

#### Japan

Japan has had a very high savings rate and a high growth rate of output per worker over the past half century, starting from an initial post-WWII very low level of capital per worker. What does the analysis suggest about Japan's ability to sustain a higher growth rate than other industrial countries?

#### Italy

Since 1946 Italian population growth (including illegal immigration) has been constant at about 1% per year and Italy has had a savings share of 25% of GDP. Today Italy has a GDP per capita level of about $25,000 per year. The rate of growth of the efficiency of labor in Italy since the end of World War II has been constant at about 2% per year. Assume that Italy is today on its steady-state balanced-growth path.

1. If Italy remains on its current steady-state balanced-growth path, what will GDP per capita be in Italy in 2050?
2. If Italy remains on its current steady-state balanced-growth path, what will GDP per capita be in France in 2100?
3. What would Italyʼs level of GDP per capita have been back in 1946 if it had then been on todayʼs steady-state balanced-growth path?
4. In fact, Italy level of GDP per capita back in 1946 was about $2,500 per year even though its efficiency of labor has grown at 2% per year since the end of World War II. Why do you think its level back then was so low?

#### Environment

Suppose that environmental regulations lead to a diversion of investment spending from investments that boost the capital stock to investments that replace polluting with less-polluting capital. In our standard growth model, what would be the consequences of such a diversion for the economy's capital-output ratio and for its balanced-growth path? Would it make sense to say that these environmental regulations diminished the economy's wealth?

#### Korea

In the 1950s, South Korea had a savings-investment share of GDP of 10%. In 1960, South Korea had a GDP per worker level of \\$2000 (at 2010 prices, in international dollars). Since 1960 South Koreaʼs savings-investment share of GDP has averaged 27.5\%. Today South Korea has a GDP per worker level of \\$40,000. In the 1950s, South Koreaʼs population growth rate averaged 3% per year. Since 1960 South Koreaʼs population growth rate has averaged 1% per year. Assume that the depreciation rate on the capital stock has been constant at 5%. Assume that the diminishing-returns parameter in the production function α=0.5. Assume that the growth rate of South Koreaʼs efficiency of labor was 0 in the 1950s, and has been constant at some positive value g since. Assume that South Korea in 1960 was in its steady-state balanced-growth path, and is today on its steady-state balanced growth path.

1. What was South Koreaʼs efficiency of labor E in 1960?
2. Suppose the rate of growth of the efficiency of labor in South Korea since 1960
has averaged 6% per year. What would be the efficiency of labor in South Korea
today?
3. Suppose the rate of growth of the efficiency of labor in South Korea since 1960
has averaged 5% per year. What would be the capital-output ratio in South Korea
today? 
4. Suppose the rate of growth of the efficiency of labor in South Korea since 1960
has averaged 5% per year. What would be the level of output per worker in South
Korea today?
5. Do you think the average growth rate of the efficiency of labor in South Korea
since 1960 has been faster or slower than 5%. Why?
6. Suppose that we have α=2/3 rather than α=0.5. How would your answers be different?

#### Korea II

Since 1960 South Koreaʼs savings-investment share of GDP has averaged 27.5%. Since 1960 the United Statesʼs savings-investment share of GDP has averaged 20%. Today South Korea has a GDP per worker level of \\$40,000. Today the United States has a GDP per worker level of \\$70,000. Since 1960 South Koreaʼs and the United Statesʼs population growth rates have both averaged 1%/year. Assume that the depreciation rate on the capital stock has been constant at 5%/year and that the rate of improvement of the efficiency of labor in the United States has averaged 2% per year. Assume that both South Korea and the United States today are on their balanced growth paths.

1. What is the efficiency of labor in South Korea today?
2. What is the efficiency of labor in the United States today?
3. If the efficiency of labor in the United States continues to grow at its long-run trend pace of 2% per year, what is your forecast of the level of output per worker in the United States in 2100?
4. What is your forecast of output per worker in South Korea in 2100?

#### Bangladesh

Bangladesh: In 1960 annual output per worker in what was to become Bangladesh averaged 1200 dollars. Today annual output per worker in Bangladesh averages $3000. If output per worker in Bangladesh continues to grow at the average pace it has grown since 1960...

1. How long will it take Bangladesh to achieve the productivity levels that South Korea has today?
2. How long will it take Bangladesh to achieve the productivity levels that the U.S. has today?
3. If output per worker in the U.S. continues to grow at its long-run historical average rate of 2 percent/year, what will output per worker in the U.S. be when Bangladesh becomes as prosperous as the United States is now?

#### Comparisons

1. Roughly, what is the gap between real per capita GDP in Belgium today, real per capita in Indonesia, and real GDP per capita in Nigeria?
2. Roughly, what is the gap between real per capita GDP in Qatar today, real per capita in Venezuela, and real GDP per capita in Nigeria?

#### Economic Growth

With the ebbing of the computer revolution and the growing worry that an increasing share of economic activity in the future will be concentrated in high labor-cost low productivity-growth sectors, many economists fear that the rate of growth of the efficiency of labor in the United States will average 1.2 percent per year in the the future rather than the 2.0 percent per year that has been the average since 1900. Assume that the rate of labor force growth remains constant at 0.8 percent per year, that the depreciation rate were to remain constant at 3 percent per year, that the year-2010 efficiency of labor in the United States was $25,000 per year, that the diminishing-returns-to-capital parameter α in the production function is 1/2, and that the American savings rate (plus foreign capital invested in America) has averaged 20 percent per year.

1. What was the level of output per worker in 2010 if the United States was then on its steady-state balanced-growth path?
2. If these fears that productivity growth will fall to 1% per year are justified, what is your forecast of the efficiency of labor in the United States in 2050?
3. If these fears that productivity growth will fall to 1% per year are justified, what is your forecast of the level of GDP per worker in the United States in 2050 if the savings rate remains at 20 percent?
4. If these fears that productivity growth will fall to 1% per year are justified, what is your forecast of the level of GDP per worker in the United States in 2050 if tax cuts and large deficits lead the savings rate to average 15 percent?
5. If these fears that productivity growth will fall to 1% per year are justified, what is your forecast of the level of GDP per worker in the United States in 2050 if wise fiscal policies and government-subsidized savings plans lead the savings rate to average 25 percent?

## Chapter 7: Circular Flows and General Gluts

#### Sources of Price Stickiness

Think about the four possible source of price stickiness: money illusion, "fairness" considerations, misperceptions of price changes, and menu costs. What have you read or seen in the past two months that strike you as examples of any of these four phenomena? Which of the four strikes you as most likely to be the most important? Be brief!—one paragraph only.

#### Institutional Sources of Price Stickiness

What changes in the economy's institutions can you think of that would diminish price stickiness and increase price flexibility? What advantage in terms of the size of the business cycle would you expect to follow from such changes in institutions? What disadvantages do you think that such institutional changes might have? (One paragraph only!)

#### Jean Baptiste Say

in 1803 claimed that because nobody makes anything without intending to use it or sell it, and nobody sells anything without intending to buy something else, that there could be no general shortage of demand in an economy-- that there could be a planned excess of supply of some commodities, but it would be balanced by a planned excess of demand of some other commodities. Was he wrong? Why was he wrong?

## Chapter 8: Building Blocks of the Flexible Price Model

## Chapter 9: Equilibrium in the Flexible Price Model

#### Adding Up National Product

In the simple income-expenditure model with real national product Y equal to the sum of consumption spending by households C, investment spending by businesses I, government purchases G, and with net exports NX; with consumption spending C given by the equation: where $Y = C + O$ and $C = co + cyY(1-t)$; and with imports IM given by the equation: $IM = imyY$...

1. Suppose C = \\$10.25 trillion, I = \\$1.68 trillion, G = \\$2.97 trillion, GX = \\$1.66 trillion, the tax rate t=0, and IM = \\$2.10 trillion. What is national product Y?
2. Suppose C = \\$3.83 trillion, the tax rate t=0, I = \\$0.86 trillion, G = \\$1.18 trillion, GX = \\$.55 trillion, and Y = \\$5.80 trillion. What is gross imports IM?
3. Suppose Suppose IM = \\$0.29 trillion, the tax rate t=0, I = \\$0.48 trillion, G = \\$0.57 trillion, GX = \\$.28 trillion, and Y = \\$2.79 trillion. What is consumption spending C?
4. Suppose Suppose IM = \\$0.02 trillion, the tax rate t=0, I = \\$0.08 trillion, G = \\$0.11 trillion, GX = \\$0.03 trillion, and C = \\$0.33 trillion. What is national product Y?

#### Adding Up National Product II

In the simple income-expenditure model with real GDP Y equal to the sum of consumption spending by households C, investment spending by businesses I, government purchases G, and with net exports NX; with consumption spending C given by the equation: $C = co + cyY(1-t)$; and with imports IM given by the equation: IM = $imyY$

1. Suppose I = \\$1.7 trillion, G = \\$3 trillion, GX = \\$1.7 trillion, co = \\$3 trillion, cy = 0.5, the tax rate t=0, and imy = .15. What is national product Y?
2. Suppose I = \\$1.7 trillion, G = \\$3.5 trillion, GX = \\$1.7 trillion, co = \\$3 trillion, cy = 0.5, the tax rate t=0, and imy = .15. What is national product Y?
3. Suppose I = \\$1.7 trillion, G = \\$4 trillion, GX = \\$1.7 trillion, co = \\$3 trillion, cy = 0.5, the tax rate t=0, and imy = .15. What is national product Y?
4. Suppose I = \\$1.7 trillion, G = \\$2.5 trillion, GX = \\$1.7 trillion, co = \\$3 trillion, cy = 0.5, the tax rate t=0, and imy = .15. What is national product Y?

#### Adding Up National Product III

In the simple income-expenditure model with real GDP Y equal to the sum of consumption spending by households C, investment spending by businesses I, government purchases G, and with net exports NX; with consumption spending C given by the equation: $C = co + cyY(1-t)$; and with imports IM given by the equation: $IM = imyY$

1. Suppose I = \\$1.8 trillion, G = \\$3 trillion, GX = \\$1.7 trillion, co = \\$3 trillion, cy = 0.5, the tax rate t=0, and imy = .15. What is GDP Y?
2. Suppose I = \\$1.8 trillion, G = \\$3.5 trillion, GX = \\$1.7 trillion, co = \\$2 trillion, cy = 1.0, the tax rate t=0.85, and imy = .15. What is GDP Y?
3. Suppose I = \\$1.7 trillion, G = \\$2 trillion, GX = \\$1.8 trillion, co = \\$3 trillion, cy = 0.65, the tax rate t=0, and imy = .15. What is GDP Y?

## Chapter 10: Money, Prices, and Inflation

#### Money Growth, Real Growth, and Inflation

Suppose that the rate of labor force growth is 1% per year and that the rate of growth of the efficiency of labor is 2% per year. Suppose also that the rate of growth of the nominal money stock is 15% per year, and there are little or no changes in how the banking system works. Do you think that it is likely that the inflation rate is less than 5% per year? Why or why not?

#### Open Market Operations

What would the Federal Reserve have to do if it wanted to raise the monetary base today by $20 billion? What do you guess would happen to the interest rate on short-term government bonds if the Federal Reserve did this?

#### "Money"

Do you think that unspent balances on credit cards--the difference between what you currently owe on your credit card and the limit that the credit card company allows you-- should be counted as "money"? Why or why not? (One sentence only!)

#### Quantity Theory of Money

Suppose that the rate of labor force growth is 1% per year, the efficiency of labor is growing at 2% per year, and the economy is on its steady state growth path. Suppose also that the trend is that the velocity of money is growing at 1% per year.

1. How fast should the Federal Reserve seek to make the growth rate of the money stock if it its inflation target is price stability--a 0% per year rate of growth of the CPI?
2. How fast should the Federal Reserve seek to make the growth rate of the money stock if it its inflation target is a 2% per year rate of growth of the CPI?
3. How fast should the Federal Reserve seek to make the growth rate of the money stock if it its inflation target is a 5% per year rate of growth of the CPI?

#### Quantity Theory of Money:

1. Suppose that the level of real potential output Y* is \\$14 trillion, the nominal money stock M is \\$2 trillion, and the velocity of money V is 7. What is the price level P?
2. Suppose that the level of real potential output Y* is \\$14 trillion, the nominal money stock M is \\$2.5 trillion, and the velocity of money V is 5. What is the price level P?
3. Suppose that the level of real potential output Y* is \\$14 trillion, the nominal money stock M is \\$4 trillion, and the velocity of money V is 7. What is the price level P?
4. Suppose that the level of real potential output Y* is \\$15 trillion, the nominal money stock M is \\$4 trillion, and the velocity of money V is 5. What is the price level P?

## Chapter 11: Consumption and the Multiplier

#### The Keynesian Cross

Consider an economy in which prices are sticky, the marginal propensity to consume out of disposable income Cy is 0.75, the tax rate t is 0.25, and the share of national income spent on imports IMy is 20 percent.

1. Suppose that total autonomous spending is \\$6 trillion. Graph planned expenditure as a function of total national income.
2. Determine the equilibrium level of national income and real product.
3. What is the value of the multiplier in this economy?
4. Suppose that total autonomous spending increases by \\$100 billion to $6.1 trillion. What happens to the equilibrium level of national income and real GDP, Y?

#### Raising and Lowering Short-Run Real Product

Classify the following set of changes into two groups: those that increase equilibrium real national product, and those that decrease real national product:

1. An increase in consumers' desire to spend today.
2. An increase in interest rates overseas.
3. A decline in foreign exchange speculators' confidence in the value of the home currency.
4. A fall in real GDP overseas.
5. An increase in government purchases.
6. An increase in managers' expectations of the future profitability of investments. g. An increase in the tax rate.

#### Boosting Real Product via Government Purchases

1. Suppose that the government wishes (for good reasons) to increase the equilibrium level of real GDP by \\$800 billion. How would you suggest that the government go about figuring out how to accomplish this goal?
2. Suppose that the economy is short of its full-employment level of GDP, \\$12 trillion, by \\$1,000 billion, with the MPC out of disposable income Cy equal to 0.6, the import share IMy equal to 0.2, and the tax rate t equal to 25%.
3. Suppose the government wants to boost real GDP up to full employment by cutting taxes. How large a cut in the tax rate is required to boost real GDP to full employment? How large a cut in total tax collections is produced by this cut in the tax rate?
4. Suppose the government wants to boost real GDP up to full employment by increasing government spending. How large an increase in government spending is required to boost real GDP to full employment?
5. Can you account for any asymmetry between your answers?

#### Shifting National Product

In the simple income-expenditure model with real national product Y equal to the sum of consumption spending by households C, investment spending by businesses I, government purchases G, and with net exports NX; with consumption spending C given by the equation: where $Y = C + O$ and $C = co + cyY(1-t)$; and with imports IM given by the equation: $IM = imyY$

1. Suppose cy = 0.5, the tax rate t=0, imy = 0.5, and G increases by \\$100 billion. What happens to GDP Y?
2. Suppose cy = 0.5, the tax rate t=0, imy = 0.16667, and G increases by \\$100 billion. What happens to GDP Y?
3. Suppose cy = 0.9, the tax rate t=0, imy = 0.1, and G increases by \\$100 billion. What happens to GDP Y?
4. Suppose cy = 0.25, the tax rate t=0, imy = 0.25, and G increases by \\$100 billion. What happens to GDP Y?

#### Shifting National Product II

In the simple income-expenditure model with real GDP Y equal to the sum of consumption spending by households C, investment spending by businesses I, government purchases G, and with net exports NX; with consumption spending C given by the equation: $C = co + cyY(1-t)$; and with imports IM given by the equation: $IM = imyY$

1. Suppose cy = 0.5, the tax rate t=0, imy = 0.5, and I increases by \\$100 billion. What happens to GDP Y?
2. Suppose cy = 0.5, the tax rate t=0, imy = 0.16667, and GX increases by \\$100 billion. What happens to GDP Y?
3. Suppose cy = 0.8, the tax rate t=0, imy = 0.05, and I increases by \\$100 billion. What happens to GDP Y?
4. Suppose cy = 0.25, the tax rate t=0, imy = 0.25, and c0 increases by \\$100 billion. What happens to GDP Y?

#### Shifting National Product III

In the simple income-expenditure model with real GDP Y equal to the sum of consumption spending by households C, investment spending by businesses I, government purchases G, and with net exports NX; with consumption spending C given by the equation: $C = co + cyY(1-t)$; and with imports IM given by the equation: $IM = imyY$

1. Suppose cy = 0.6, the tax rate t=0, imy = 0.1, and I falls by \\$250 billion. What happens to national product Y?
2. Suppose cy = 0.6, the tax rate t=0.2, imy = 0.1, and I falls by \\$250 billion. What happens to national product GDP Y?
3. Suppose cy = 0.6, the tax rate t=0.4, imy = 0.1, and I falls by \\$250 billion. What happens to national product GDP Y?
4. Suppose cy = 0.6, the tax rate t=0.6, imy = 0.1, and I falls by \\$250 billion. What happens to national product GDP Y?
5. Since the 1930s, left-wing economists have argued that an economy with a higher share of government spending and taxes in GDP is less vulnerable to business cycle downturns. Why might this be so?

#### Shifting National Product IV

In the simple income-expenditure model with real GDP Y equal to the sum of consumption spending by households C, investment spending by businesses I, government purchases G, and with net exports NX; with consumption spending C given by the equation: $C = co + cyY(1-t)$; and with imports IM given by the equation: $IM = imyY$

1. Suppose cy = 0.6, the tax rate t=0.2, imy = 0.0, and G rises by \\$250 billion. What happens to GDP Y?
2. Suppose cy = 0.6, the tax rate t=0.2, imy = 0.1, and G rises by \\$250 billion. What happens to GDP Y?
3. Suppose cy = 0.6, the tax rate t=0.2, imy = 0.2, and G rises by \\$250 billion. What happens to GDP Y?
4. Suppose cy = 0.6, the tax rate t=0.2, imy = 0.3, and G rises by \\$250 billion. What happens to GDP Y?
5. Since the 1940s, economists have argued that as world trade and the propensity to import rise, government spending becomes less effective as a tool for boosting production and fighting depressions. Why might this be so?

#### Shifting National Product V

In the simple income-expenditure model with real GDP Y equal to the sum of consumption spending by households C, investment spending by businesses I, government purchases G, and with net exports NX; with consumption spending C given by the equation: $C = co + cyY(1-t)$; and with imports IM given by the equation: $IM = imyY$

1. Suppose cy = 0.4, the tax rate t=0.2, imy = 0.2, and I falls by \\$200 billion. What happens to national product Y?
2. Suppose cy = 0.6, the tax rate t=0.2, imy = 0.2, and I falls by \\$200 billion. What happens to national product Y?
3. Suppose cy = 0.8, the tax rate t=0.2, imy = 0.2, and I falls by \\$200 billion. What happens to national product Y?
4. Suppose cy = 1.0, the tax rate t=0.2, imy = 0.2, and I falls by \\$200 billion. What happens to national product Y?

## Chapter 12: The Investment and Savings Curve

#### TFU

Label each of the following statements as True, False, or Uncertain, and explain your answer briefly.

1. In the short run, an increase in consumer confidence raises the real interest rate, consumption, and real GDP.
2. The fact that the U.S. output growth was only slightly less volatile in the four decades or so after World War 2 than in the four decades or so before the Great Depression shows that fiscal and monetary policy do not have large short-run effects on output.
3. If consumers decide to save more at a given level of disposable income than before, investment will rise, and so output will rise.

#### IS Equilibrium: Tax Increase

Suppose there is a tax increase.

1. In the simple IS-MP model with a single real interest rate, does consumption rise, fall,
stay the same, or is it impossible to tell? Does investment rise, fall, stay the same, or is it
impossible to tell?
2. In the IS-MP model with an interest rate differential, does consumption rise, fall, stay
the same, or is it impossible to tell? Does investment rise, fall, stay the same, or is it impossible to tell?

#### True, False, or Uncertain, and explain your answer briefly:

1. “In the IS-MP model extended to include an interest rate differential, an increase in confidence in the soundness of the financial system increases output.”
2. “Introducing an interest rate differential into the IS-MP model makes the AD curve steeper than it otherwise would be.”
3. “If the fiscal policy multiplier is less than 1, then fiscal policy cannot help to end a recession.”

#### Pick the Best Answer

1. Researchers who are trying to estimate the effects of changes in government purchases on real GDP often focus on military purchases because: a. The types of government purchases that policymakers are likely to use to combat a recession are similar in important ways to military purchases. b. Wars are often accompanied by price controls, which makes them particularly good times for isolating the effects of changes in government purchases. c. Changes in military purchases are caused mainly by geopolitical developments outside the United Sates, not by other factors affecting U.S. GDP. d. It is hard to obtain data on non-military purchases.
2. “asset price bubble” means: a. A large, rapid rise in asset prices. b. A rise in asset prices that is reversed.c. A rise in asset prices in response to reductions in interest rates. d. Asset prices being greater than their “fundamental” values.
3. Suppose a variable, y, is determined by a factor we can measure, x, and by other factors that we cannot. That is, y = a + bx + e, where a and b are parameters and e is the unobserved other factors. Estimates of b from a regression of y on x (estimated by “ordinary least squares”) will tend to overestimate the impact of x on y if: a. x and e are negatively correlated (that is, e tends to be low when x is high, and high when x is low). b. x and e are uncorrelated (that is, x has no consistent relationship with e). c. x and e are positively correlated (that is, e tends to be high when x is high, and low when x is low). d. a and x are positively correlated.
4. The fact that the bankruptcy of Lehman Brothers nearly caused the failure of institutions that had made loans to Lehman Brothers is an example of: a. “Confidence” contagion. b. “Coordination” or “Fire sale” contagion. c. “Counterparty” contagion. d. None of the above.
5. The “borrowing” interest rate, rb, is usually higher than the “saving” interest rate, rs, because: a. Financial intermediaries’ information production, liquidity transformation, and diversification provision are costly. b. Government regulations limit the interest rates that banks can pay. c. The interest rates that foreigners can get on their savings are generally lower than interest rates in the United States. d. The inflation rate faced by savers is usually lower than the inflation rate faced by borrowers.

#### Income-Spending Shifts

Consider ΔY = [ΔA0 + ΔG - (Ir + Xεεr)Δr]/(1-(1-t)cy + imy), the investment savings framework (with ΔA0 = Δc0 + ΔI0 -XεΔε0 + Xy*ΔY* + XεεrΔr). Suppose the multiplier 1/(1-(1-t)cy + imy) = 1.5 and the responsiveness of exports to the exchange rate Xε = 500...

1. What happens to Y if government purchases G goes up by \\$100 billion, and nothing else changes?
2. What happens to Y if baseline investment spending I0 goes up by \\$100 billion, and nothing else changes?
3. What happens to Y if baseline consumption spending c0 goes up by \\$100 billion, and nothing else changes?
4. What happens to Y if speculator confidence in the currency ε0 goes up by 20%— by 0.2—and nothing else changes?
5. Explain the similarities and the differences between your answers to (a)-(d).

#### Income-Spending Shifts II

Consider ΔY = [ΔA0 + ΔG - (Ir + Xεεr)Δr]/(1-(1-t)cy + imy), the investment savings framework (with ΔA0 = Δc0 + ΔI0 -XεΔε0 + Xy*ΔY* + XεεrΔr). Suppose the multiplier 1/(1-(1-t)cy + imy) = 1.5 and the responsiveness of exports to the exchange rate Xε = 500...

1. Suppose that capital controls keep the exchange rate from responding to changes in the interest rate—suppose that εr = 0—and suppose the sensitivity of investment spending to the interest rate Ir = 50. If the interest rate falls by 2%—by 200 basis points, or by 0.02—what happens to Y?
2. Suppose that the responsiveness of the exchange rate to changes in the interest εr = 1, and suppose the sensitivity of investment spending to the interest rate Ir = 50. If the interest rate falls by 2%—by 200 basis points, or by 0.02—what happens to Y?
3. Suppose that the responsiveness of the exchange rate to changes in the interest εr = 5, and suppose the sensitivity of investment spending to the interest rate Ir = 50. If the interest rate falls by 2%—by 200 basis points, or by 0.02—what happens to Y?
4. Suppose that the responsiveness of the exchange rate to changes in the interest εr = 20, and suppose the sensitivity of investment spending to the interest rate Ir = 50. If the interest rate falls by 2%—by 200 basis points, or by 0.02—what happens to Y?
5. Explain the similarities and the differences between your answers to (a)-(d). What features of the situation besides government controls on foreign investment might influence the value of εr?

#### Income-Spending Shifts III

Consider ΔY = [ΔA0 + ΔG - (Ir + Xεεr)Δr]/(1-(1-t)cy + imy), the investment savings framework (with ΔA0 = Δc0 + ΔI0 -XεΔε0 + Xy*ΔY* + XεεrΔr). Suppose the multiplier 1/(1-(1-t)cy + imy) = 1.5, the responsiveness of exports to the exchange rate Xε = 500, and the responsiveness of the exchange rate to changes in the interest εr = 10...

1. What happens to Y if the real interest rate r goes up by 1%—by 100 basis points or by 0.01?
2. What happens to Y if the real interest rate r goes up by 1%—by 100 basis points or by 0.01—and if baseline investment spending goes up by 50?
3. What happens to Y if the real interest rate r goes down by 1%—by 100 basis points or 0.01—and if speculator confidence in the currency goes up by 10%?
4. What happens to Y if the real interest rate r goes up by 1%—by 100 basis points or by 0.01— and if baseline consumption spending goes down by 50?

#### Income-Spending Shifts IV

Consider ΔY = [ΔA0 + ΔG - (Ir + Xεεr)Δr]/(1-(1-t)cy + imy), the investment savings framework (with ΔA0 = Δc0 + ΔI0 -XεΔε0 + Xy*ΔY* + XεεrΔr). Suppose the multiplier 1/(1-(1-t)cy + imy) = 1.5 and the responsiveness of exports to the exchange rate Xε = 500...

1. What happens to Y if the real interest rate r goes up by 2%—by 100 basis points or by 0.01—and if speculator confidence in the currency goes down by 20%?
2.  What happens to Y if the real interest rate r goes up by 1%—by 100 basis points or by 0.01—and if baseline investment spending goes down by 200?
3. What happens to Y if the real interest rate r goes down by 1%—by 100 basis points or 0.01—and if speculator confidence in the currency goes up by 5%?
4. What happens to Y if the real interest rate r goes up by 1%—by 100 basis points or by 0.01— and if baseline consumption spending goes up by 100?
5.  How would your answers to (8) be different if instead of 1/(1-(1-t)cy + imy) = 1.5, t=0.25, cy =0.8 imy=0.1?

#### Income-Spending Shifts V

Consider ΔY = [ΔA0 + ΔG - (Ir + Xεεr)Δr]/(1-(1-t)cy + imy), the investment savings framework (with ΔA0 = Δc0 + ΔI0 -XεΔε0 + Xy*ΔY* + XεεrΔr). Suppose the multiplier 1/(1-(1-t)cy + imy) = 1.5 and the responsiveness of exports to the exchange rate Xε = 500...

1. Why does a contractionary monetary policy abroad that raises interest rates abroad raise GDP at home?
2. Why does an outburst of enthusiasm among foreign exchange speculators that makes them more confident about the long-run value of the home currency reduce GDP at home?
3. When an outburst of enthusiasm among foreign exchange speculators that makes them more confident about the long-run value of the home currency reduces GDP at home, what components of GDP change and in which direction?
4. What would be the effects on GDP at home of a stimulative fiscal policy abroad that raised real GDP abroad?

#### International Shocks

Consider ΔY = [ΔA0 + ΔG - (Ir + Xεεr)Δr]/(1-(1-t)cy + imy), the investment savings framework (with ΔA0 = Δc0 + ΔI0 -XεΔε0 + XyfΔYf + XεεrΔrf). Suppose the responsiveness of exports to the exchange rate Xε = 500, the responsiveness of the exchange rate to interest rates εr=10, and the responsiveness of investment to the interest rate Ir = 1000. And suppose t=0.2, cy =0.8 imy=0.14:

1. What happens to Y if the real interest rate r goes up by 2%—by 0.02—and if speculator confidence in the currency goes down by 30%?
2. What happens to Y if the real interest rate r goes up by 1%—by 0.01—and if baseline investment spending goes down by 300?
3. What happens to Y if the real interest rate r goes down by 1%—by 0.01—and if speculator confidence in the currency goes up by 5

#### Depression Economic

In the simple income-expenditure model with real GDP Y equal to the sum of consumption spending by households C, investment spending by businesses I, government purchases G, and with net exports NX; with consumption spending C given by the equation: C = co + cyY(1-t); and with imports IM given by the equation: IM = imyY...

1. Suppose I = \\$1.7 trillion, G = \\$2 trillion, GX = \\$1.3 trillion, co = \\$3 trillion, cy = 0.85, the tax rate t=0, and imy = .10. What is GDP Y?
2. Suppose I = \\$1.7 trillion, G = \\$3.5 trillion, GX = \\$0.8 trillion, co = \\$3 trillion, cy = 0.65, the tax rate t=0, and imy = .15. What is GDP Y?
3. Suppose I = \\$2.3 trillion, G = \\$4 trillion, GX = \\$1.7 trillion, co = \\$3 trillion, cy = 0.6, the tax rate t=0.67, and imy = .2. What is GDP Y?
4. Suppose I = \\$1.5 trillion, G = \\$2.5 trillion, GX = \\$1.0 trillion, co = \\$3 trillion, cy = 0.67, the tax rate t=0, and imy=.0. What is GDP Y?

## Chapter 13: Financial Crises

#### Financial Crisis

This problem asks you to perform an event study. In the extension of the IS-MP-IA model to include an interest rate differential, a financial crisis is assumed to raise the differential. This problem therefore asks you to investigate whether interest rate differentials (often referred to as interest rate spreads) rose at the time of some of the major events associated with the financial crisis in the fall of 2008.

Specifically, consider the difference between the interest rates on BAA corporate bonds and on 30-year Treasury bonds. And consider any 3 of the following 4 events, all of which occurred in September 2008: (1) The government takeover of Fannie Mae and Freddie Mac; (2) Lehman Brothers’ announcement that it would file for bankruptcy; (3) The government takeover of AIG; (4) The House of Representatives’ rejection of the initial TARP legislation. (Note: no extra credit for considering all 4 events.)
a.
1. For each event that you chose, find the day that it occurred. As far as you can tell, did it occur when financial markets were open (which, loosely speaking, corresponds to normal working hours in New York) or when they were closed? Describe how you found this information and how confident you are about it.
2. For each event, if it occurred when financial markets were open, find the change in the interest rate spread on the day of the event. If financial markets were closed, find the change in the spread on the next day of trading. Did these events lead to noticeable increases in the interest rate spread? Be sure to describe where you found your data.
3. What was the overall change in the spread from the end of August 2008 to the end of October 2008?
4. For many economic relationships (for example, between money and output), we would not expect a big effect in a day. Explain why one might or might not expect the worsening of a financial crisis to have a noticeable impact on interest rate spreads in a day.

#### Risky Interest Rates

Our model with an interest rate differential assumes that all investment depends on a single interest rate, rb. In truth, there are many interest rates, and they are relevant to many different kinds of investment.

To partially capture this idea, suppose investment is the sum of two types of investment, a safer type I1 and a riskier type I2. I1 depends on rb1 and I2 depends on rb2: I1 = I1(rb1), I2 = I2(rb2), where both functions are decreasing. Suppose also that rb1 – rs = d1(Y) and rb2 – rs = d2(Y), again with both functions decreasing. To reflect the idea that Type 2 investment is riskier than Type 1 investment, assume that for a given Y, rb2 – rs is greater than rb1 – rs, and that when Y falls, rb2 – rs rises by more than rb1 – rs does.

1. In this model, suppose there is a fall in consumer confidence, so that C for a given Y – T is lower than before.
i. What is the effect of this change on rs, Y, rb1 – rs, and rb2 – rs? ii. Is the change in rb1 – rs larger, smaller, or the same as the change in rb2 – rs, or is it not possible to tell?
2. One message we have stressed is that a modeling assumption is not inherently “good” or “bad”; the value of an assumption depends on the question we are trying to answer. Thus, give one example of a question that moving from a model with just one interest rate differential (rb – rs) to one with two differentials (rb1 – rs and rb2 – rs) would be helpful in answering. Give one example of a question where moving from a model with one differential to a model with two would complicate the analysis without generating any significant additional insights.

#### Debt and Vulnerability

Recent research stresses the role of high levels of debt for consumers and firms in causing or exacerbating short-run fluctuations.

1. What is some of the evidence that high levels of debt affect consumer or firm behavior?
2. If consumers and firms are trying to reduce their debt (deleverage), how, if at all, is this likely to show up in the IS-MP diagram? Why?
3. What policy actions would be most effective in combating a recession caused by deleveraging? Why?

#### True, False, or Uncertain, and explain your answer briefly

1. “The bursting of an asset price bubble can lead to a financial crisis.”
2. “High income inequality can result in a long-lasting shortfall of aggregate demand and very prolonged high unemployment.”
  

#### The Eurozone

Both Iceland and Ireland suffered major banking crises starting around September 2008. One potentially important difference between the two countries is that Ireland is a member of the Eurozone while Iceland has its own currency:

1. By how much did the Icelandic Króna depreciate against the euro from August 2008 to its low point? How much lower is the Króna against the euro today than it was in August 2008?
2. By how much did the unemployment rate rise, in percentage points, in Iceland from its pre-crisis level to its peak? By how much did it rise in Ireland?
3. If the exchange rate was important to the different performances of the two countries, we would expect that to be reflected in the behavior of net exports. Is the behavior of net exports in the two countries consistent with the hypothesis that exchange rate depreciation helped to cushion the effects of the banking crisis in Iceland?
Pick the best answer to each of questions 5–8. No explanations of your answers are needed.

#### Financial Panics in the Great Depression

In the paper by Richardson and Troost on banking panics in Mississippi, the authors find that the monetary policy beliefs and behavior of the Federal Reserve Banks of Atlanta and St. Louis were:

1. Fundamentally different before, during, and after the panics of 1930.
2. Different in the 1920s, but very similar starting in 1929.
3. Similar throughout the 1920s and 1930s.
4. Very different before and during the panic of 1930, but similar during later panics in
the Depression.

#### "Uncertainty"

Uncertainty is likely to have an especially large negative short-run effect on spending by households and firms if:

1. They do not expect the uncertainty to be resolved soon.
2. There are large costs to reversing their spending decisions. 
3. The real interest rate is high.
4. Inflation is high.
5. All of the above.
6. None of the above.

#### Financial Sophistication

In 1986 your lecturer Brad DeLong and Lawrence Summers wrote a paper in which they argued that the coming of more sophisticated financial markets—in which households could borrow and repay easily and did not have to respond to a \\$1 decline in their incomes by cutting their consumption spending by a large fraction of \\$1—would be less vulnerable to business cycle downturns. It now looks as though we were catatrophically wrong. But why did we think this back then?

## Chapter 14: Liquidity and Money

## Chapter 15: The Phillips Curve, Expectations, and Monetary Policy

#### Adaptive Expectations

Suppose that the economy's Phillips curve is given by:

>u = u' − β(π − πe)

with β equal to 0.5 and the natural rate of unemployment u' equal to 5 percent. Suppose that the economy has for a long time had a constant inflation rate π equal to 2 percent per year. Suddenly the government announces a new policy: it will use fiscal policy to push the unemployment rate down by 2 percentage points--and promises it will keep that expanded fiscal policy in place indefinitely.

Suppose, further that the dominant way of forming expectations in the economy is such that people have adaptive expectations of inflation--so that this year's expected inflation is equal to last year's actual inflation. What will be the course of inflation and unemployment in this economy in the years after the shift in fiscal policy? Track the economy out ten years, assuming that there are no additional shocks.

#### Rational Expectations

Suppose that the economy's Phillips curve is given by:

>u = u' − β(π − πe)

with β equal to 0.5 and the natural rate of unemployment u' equal to 5 percent. Suppose that the economy has for a long time had a constant inflation rate π equal to 2 percent per year. Suddenly the government announces a new policy: it will use fiscal policy to push the unemployment rate down by 2 percentage points--and promises it will keep that expanded fiscal policy in place indefinitely.

Suppose further that agents in the economy have rational expectations of inflation--so that this year's expected inflation is what an economist knowing the structure of the economy and proposed economic policies would calculate actual inflation was likely to be. What will be the course of inflation and unemployment in this economy in the years after the shift in fiscal policy? Track the economy out twenty years, assuming that there are no additional shocks.

#### The Sacrifice Ratio

Suppose that an economy starts at an initial inflation level π0 and that its central bank seeks to reduce inflation down to some final level πT by pushing the unemployment rate u up above the natural rate of unemployment u'. Suppose that the relationship between inflation and unemployment is given by the adaptive-expectations Phillips Curve equation:

>π = π−1+β(u'−u)

where β is a known parameter. Let U stand for the total cumulative excess of € unemployment over the natural rate needed to accomplish this policy. 

Solve, algebraically, for the total cumulative excess unemployment U. In what units is U measured? Suppose that you are asked to calculate the sacrifice ratio S/( π0- πT). How is the sacrifice ratio related to the parameter β in the Phillips Curve? Write a paragraph explaining how you would go about deciding whether the policy of reducing inflation through higher-than-natural unemployment is a good one or a bad one.

#### Quantity Theory of Money

Suppose that the rate of labor force growth is 3% per year, the efficiency of labor is constant, and the economy is on its steady state growth path. Suppose also that the rate of growth of the nominal money stock is 10% per year. Do you think that it is likely that the inflation rate is less than 5% per year? Why or why not?

#### Phillips Curve

In the Phillips Curve framework in which π = E(π) + β(un - u)—the inflation rate π equals the previously-expected inflation rate E(π) plus the Phillips Curve slope parameter β times the difference between the economy's natural rate of unemployment un and the current rate of unemployment u...

1. If E(π) = 9% per year, u* = 6%, and u = 8%, what is the inflation rate π going to be if the Phillips Curve slope parameter β = 1/2?
2. If E(π) = 3% per year, u* = 4%, and u = 4%, what is the inflation rate π going to be if the Phillips Curve slope parameter β = 1/2?
3. If E(π) = 1% per year, u* = 7%, and u = 3%, what is the inflation rate π going to be if the Phillips Curve slope parameter β = 1/3?
4. If E(π) = 1% per year, u* = 7%, and u = 3%, what is the inflation rate π going to be if the Phillips Curve slope parameter β = 2/3?
5. If E(π) = 1% per year, u* = 7%, and u = 3%, what is the inflation rate π going to be if the Phillips Curve slope parameter β = 1?

#### Monetary Policy

Suppose we have an economy with a natural rate of unemployment of 6%, current expected inflation of 2%, and a Phillips Curve slope parameter of 1/2. Suppose that the Federal Reserve has a target ut for the unemployment rate and a target πT for the inflation rate, and suppose that for each percentage point inflation is above its target level the Federal Reserve raises unemployment by an extra percentage point above its target level.

1. If the target for the inflation rate is 2% and the target for the unemployment rate is 6%, what will inflation and unemployment be?
2. If the target for the inflation rate is 3% and the target for the unemployment rate is 4%, what will inflation and unemployment be?
3. If the target for the inflation rate is 6% and the target for the unemployment rate is 8%, what will inflation and unemployment be?
4. If the target for the inflation rate is 4% and the target for the unemployment rate is 4%, what will inflation and unemployment be?

#### Monetary Policy II

Suppose we have an economy with a natural rate of unemployment of 4%, current expected inflation of 15%, and a Phillips Curve slope parameter of 1/2. Suppose that the Federal Reserve has a target u0 for the unemployment rate and a target πt for the inflation rate, and suppose that for each percentage point inflation is above its target level the Federal Reserve raises unemployment by an extra two percentage points above its target level.

1. Suppose that from this year forward the Federal Reserve sets its target for the inflation rate at 3% and its target for the unemployment rate at 5%, what will inflation and unemployment be this year?
2. Suppose expected inflation is adaptive in that each year's expected inflation is the previous year's actual inflation. What will inflation and unemployment be next year?
3. Suppose expected inflation is adaptive in that each year's expected inflation is the previous year's actual inflation. What will inflation and unemployment be two years from now?
4. Suppose expected inflation is adaptive in that each year's expected inflation is the previous year's actual inflation. What will inflation and unemployment be five years from now?
5. Suppose expected inflation is adaptive in that each year's expected inflation is the previous year's actual inflation. What will inflation and unemployment be ten years from now?

#### Monetary Policy III

Suppose we have an economy with a natural rate of unemployment of 4%, and a Phillips Curve slope parameter of 1. Suppose that the Federal Reserve has a target u0 for the unemployment rate and a target πt for the inflation rate, and suppose that for each percentage point inflation is above its target level the Federal Reserve raises unemployment by an extra two percentage points above its target level.

1. If the Federal Reserve's target for the inflation rate is 2% and its target for the unemployment rate is 4%, what will the long run rate of inflation be?
2. If the Federal Reserve's target for the inflation rate is 2% and its target for the unemployment rate is 6%, what will the long run rate of inflation be?
3. If the Federal Reserve's target for the inflation rate is 4% and its target for the unemployment rate is 4%, what will the long run rate of inflation be?
4. If the Federal Reserve's target for the inflation rate is 4% and its target for the unemployment rate is 8%, what will the long run rate of inflation be?

#### Phillips Curve

In the Phillips Curve framework in which π = E(π) + β(u* - u)—the inflation rate π equals the previously-expected inflation rate E(π) plus the Phillips Curve slope parameter β times the difference between the economy's natural rate of unemployment u* and the current rate of unemployment u...

1. If E(π) = 2% per year, u* = 6%, and u = 10%, what is the inflation rate π going to be if the Phillips Curve slope parameter β = 1/2?
2. If E(π) = 3% per year, u* = 4%, and u = 6%, what is the inflation rate π going to be if the Phillips Curve slope parameter β = 1/2?
3. If E(π) = 6% per year, u* = 7%, and u = 3%, what is the inflation rate π going to be if the Phillips Curve slope parameter β = 1/3?
4. If E(π) = 1% per year, u* = 7%, and u = 9%, what is the inflation rate π going to be if the Phillips Curve slope parameter β = 2/3?
5. If E(π) = 4% per year, u* = 8%, and u = 5%, what is the inflation rate π going to be if the Phillips Curve slope parameter β = 1?

#### Phillips Curve

In the Phillips Curve framework in which π = E(π) + β(u* - u)— the inflation rate π equals the previously-expected inflation rate E(π) plus the Phillips Curve slope parameter β times the difference between the economy's natural rate of unemployment u* and the current rate of unemployment u...

1. IfE(π)=9%peryear,u*=6%,andu=8%,whatistheinflationrateπ going to be if the Phillips Curve slope parameter β = 1/2?
2. IfE(π)=3%peryear,u*=4%,andu=4%,whatistheinflationrateπ going to be if the Phillips Curve slope parameter β = 1/2?
3. IfE(π)=1%peryear,u*=7%,andu=3%,whatistheinflationrateπ going to be if the Phillips Curve slope parameter β = 1/3?
4. IfE(π)=1%peryear,u*=7%,andu=3%,whatistheinflationrateπ going to be if the Phillips Curve slope parameter β = 2/3?
5. IfE(π)=1%peryear,u*=7%,andu=3%,whatistheinflationrateπ going to be if the Phillips Curve slope parameter β = 1?

#### Phillips Curve

In the Phillips Curve framework in which π = E(π) + β(u* - u)— the inflation rate π equals the previously-expected inflation rate E(π) plus the Phillips Curve slope parameter β times the difference between the economy's natural rate of unemployment u* and the current rate of unemployment u...

1. Suppose that the economy starts out with an expected rate of inflation of 2%/year, a Phillips Curve slope parameter of 1/2, and a natural rate of unemployment of 5%. Suppose that the Federal Reserve decides to reduce the rate of unemployment to 3% through expansionary monetary policy and does so. What is the inflation rate?
2. Now look one year ahead to next year. Next year, expectations of inflation will be adaptive: that is, expectations of inflation next year will be equal to what inflation was this year. What will expectations of inflation be next year?
3. What will actual inflation be next year if the Federal Reserve continues to pursue expansionary monetary policies to keep the rate of unemployment at 3%?
4. If inflation expectations continue to be adaptive in this sense that each year's expected is the previous year's actual inflation, what will actual inflation be two years from now?
5. If inflation expectations continue to be adaptive and if the Federal Reserve continues to follow policies to keep the unemployment rate at 3%, what will actual inflation be five years from now?
6. If inflation expectations continue to be adaptive and if the Federal Reserve continues to follow policies to keep the unemployment rate at 3%, what will actual inflation be ten years from now?
7. If inflation expectations continue to be adaptive and if the Federal Reserve continues to follow policies to keep the unemployment rate at 3%, what will actual inflation be twenty years from now?
8. . Do you think that inflation expectations will continue to be adaptive in this sense as this process rolls forward over the next twenty years, or do you think the process by which expectations of inflation are formed will change? e. If you think it will change, what do you think it will change to?


## Chapter 16: Stabilization Policy

#### Monetary vs. Fiscal Policy

Why do economists today tend to believe that monetary policy is superior to discretionary fiscal policy as a stabilization policy tool? In what circumstances that you can imagine would this belief be reversed? (One paragraph only!)

#### Raising Investment

Suppose that the government and central bank together want to keep GDP constant but raise the rate of investment. What policies can they follow to achieve this? (One sentence only!)

#### Credibility

Former Federal Reserve Vice Chair Alan Blinder has remarked that Alan Greenspan’s policies at fighting unemployment have been much more aggressive in attempting to reduce unemployment than any Federal Reserve Chair with less of a reputation as an inflation hawk would dare attempt. Can you make sense of this remark?

#### Reputation

Suppose that you believe that investors, businesses, and workers in your economy have rational expectations of inflation. Suppose that you have a choice between two candidates to head your central bank—one of whom believes that the central bank must always do whatever is necessary to keep inflation low, and the other of whom believes that if the central bank were to push unemployment above the natural rate to try to reduce inflation it would be making a serious mistake. Which candidate would you prefer to run your central bank, and why?

#### Sticky Price Output and  Interest Rates

Describe how, if at all, each of the following developments affects the real interest rate and output in the short run (or whether it is not possible to tell). In parts (1) and (2), assume that the central bank is following an interest rate rule; in parts (3) and (4), use the information in the question to decide what assumption to make about how monetary policy is being conducted:

1. The government cuts taxes.
2. The government cuts taxes and government purchases by equal amounts.
3. The government cuts taxes and, at the same time, the central bank changes its monetary policy rule so that it sets a lower real interest rate at a given level of output than before.
4. The central bank lowers its target for the money stock.

#### Monetary Policy Rules

Suppose the central bank changes its policy rule to respond more to changes in output. Specifically, it decides not to change the real interest rate at the current level of output, but that it will increase it by more than before if output rises, and cut it by more than before if output falls:

1. Would you use the IS–MP or IS–LM model to analyze the effects of this development? Why?
2. How, if at all, would this development affect the two curves (IS and MP, or IS and LM)? Explain your reasoning.
3. Suppose that after this change in the monetary policy rule, firms become more optimistic about the profitability of investment projects, so investment demand at a given real interest rate is higher than before. How, if at all, does this change affect the real interest rate and output in the short run? For each variable (r and Y), is the effect larger than before the change in the rule, smaller, the same, or is it impossible to tell?

#### Shocks Requriring Stabilization

Describe how, if at all, each of the following developments affects real output, the exchange rate, and net exports in the short run. Assume the central bank is following an interest rate rule…

1. The discovery of new investment opportunities causes investment demand to be higher at a given interest rate than before.
2. The central bank changes its monetary policy rule so that it sets a lower real interest rate at a given level of output than before.
3. The demand for money increases (that is, consumers’ preferences change so that at a given level of i and Y they want to hold more real balances than before).

#### Real Business Cycles

Consider our usual IS-MP-IA model, starting in long-run equilibrium. Suppose that potential output falls because of reduced productivity.
1. How, if at all, would this change show up in the IS-MP diagram in the short run?
2. What will be the impact of the fall in   on output and inflation in the long run?

#### Econometrics

Explain in a few sentences, without using any math, what is wrong with the following argument: “I obtained annual data on money growth and output growth, and then estimated the OLS regression Δ ln Y = a + b Δ ln M + u. After running the regression, I computed the correlation between money growth and the regression residual. It was exactly zero. Thus, since there is no correlation between the right-hand side variable and the residual, I know that my regression does not suffer from omitted-variable bias.

#### Monetary Policy

Suppose we have an economy with a natural rate of unemployment of 6%, current expected inflation of 4%, and a Phillips Curve slope parameter of 1/2. Suppose that the Federal Reserve has a target u0 for the unemployment rate and a target πt for the inflation rate.

1. If the target for the inflation rate is 4% and the target for the unemployment rate is 6%, what will inflation and unemployment be?
2. If the target for the inflation rate is 2% and the target for the unemployment rate is 6%, what will inflation and unemployment be if for each extra percentage point of inflation the Federal Reserve raises unemployment by an extra two percentage points?
3. If the target for the inflation rate is 2% and the target for the unemployment rate is 6%, what will inflation and unemployment be if for each extra percentage point of inflation the Federal Reserve raises unemployment by an extra half a percentage point?
4. If the target for the inflation rate is 2% and the target for the unemployment rate is 6%, what will inflation and unemployment be if for each extra percentage point of inflation the Federal Reserve raises unemployment by an extra percentage point?

#### Monetary Policy

Suppose we have an economy with a natural rate of unemployment of 6%, current expected inflation of 10%, and a Phillips Curve slope parameter of 1/2. Suppose that the Federal Reserve has a target u0 for the unemployment rate and a target πt for the inflation rate, and suppose that for each percentage point inflation is above its target level the Federal Reserve raises unemployment by an extra percentage point above its target level.

1. Suppose that from this year forward the Federal Reserve sets its target for the inflation rate at 3% and its target for the unemployment rate at 5%, what will inflation and unemployment be this year?
2. Suppose expected inflation is adaptive in that each year's expected inflation is the previous year's actual inflation. What will inflation and unemployment be next year?
3. Suppose expected inflation is adaptive in that each year's expected inflation is the previous year's actual inflation. What will inflation and unemployment be two years from now?
4. Suppose expected inflation is adaptive in that each year's expected inflation is the previous year's actual inflation. What will inflation and unemployment be five years from now?
5. Suppose expected inflation is adaptive in that each year's expected inflation is the previous year's actual inflation. What will inflation and unemployment be ten years from now?

#### Monetary Policy

Suppose we have an economy with a natural rate of unemployment of 6%, and a Phillips Curve slope parameter of 1/2. Suppose that the Federal Reserve has a target u0 for the unemployment rate and a target πt for the inflation rate, and suppose that for each percentage point inflation is above its target level the Federal Reserve raises unemployment by an extra two percentage points above its target level.

1. If the Federal Reserve's target for the inflation rate is 2% and its target for the unemployment rate is 4%, what will the long run rate of inflation be?
2. If the Federal Reserve's target for the inflation rate is 2% and its target for the unemployment rate is 6%, what will the long run rate of inflation be?
3. If the Federal Reserve's target for the inflation rate is 4% and its target for the unemployment rate is 4%, what will the long run rate of inflation be?
4. If the Federal Reserve's target for the inflation rate is 4% and its target for the unemployment rate is 8%, what will the long run rate of inflation be?

#### Monetary Policy

Suppose we have an economy with a natural rate of unemployment of 6%, current expected inflation of 2%, and a Phillips Curve slope parameter of 1/2. Suppose that the Federal Reserve has a target ut for the unemployment rate and a target πt for the inflation rate, and suppose that for each percentage point inflation is above its target level the Federal Reserve raises unemployment by an extra percentage point above its target level.
1. If the target for the inflation rate is 2% and the target for the unemployment rate is 6%, what will inflation and unemployment be?
2. If the target for the inflation rate is 3% and the target for the unemployment rate is 4%, what will inflation and unemployment be? 
3. If the target for the inflation rate is 6% and the target for the unemployment rate is 8%, what will inflation and unemployment be? 4. If the target for the inflation rate is 4% and the target for the unemployment rate is 4%, what will inflation and unemployment be?

#### Monetary Policy

Suppose we have an economy with a natural rate of unemployment of 6%, current expected inflation of 10%, and a Phillips Curve slope parameter of 1/2. Suppose that the Federal Reserve has a target ut for the unemployment rate and a target πt for the inflation rate, and suppose that for each percentage point inflation is above its target level the Federal Reserve raises unemployment by an extra percentage point above its target level.

1. Suppose that from this year forward the Federal Reserve sets its target for the inflation rate at 2% and its target for the unemployment rate at 4%, what will inflation and unemployment be this year?
2. Suppose expected inflation is adaptive in that each year's expected inflation is the previous year's actual inflation. What will inflation and unemployment be next year?
3. Suppose expected inflation is adaptive in that each year's expected inflation is the previous year's actual inflation. What will inflation and unemployment be two years from now?
4. Suppose expected inflation is adaptive in that each year's expected inflation is the previous year's actual inflation. What will inflation and unemployment be five years from now?
5. Suppose expected inflation is adaptive in that each year's expected inflation is the previous year's actual inflation. What will inflation and unemployment be ten years from now?

## Chapter 17: The Liquidity Trap

#### DeLong and Summers (1992)

The fact that the central bank cannot push the short-term nominal interest rate below zero raises the possibility of a liquidity trap—an inability of the central bank to push the long-term real interest rate down to a level that produces enough investment to get full employment. Back in 1992 Brad DeLong and Larry Summers argued that this made it desirable for the Federal Reserve to have an inflation target of 4-5% per year rather than 1-2% per year: the higher inflation target, you see, would give the Federal Reserve more ability to reduce the long-term real interest rate when necessary. The Fed didn’t think much of this argument. What do you think of it?

## Chapter 18: The Government Debt

## Chapter 19: Secular Stagnation

#### Secular Stagnation

The three “coping mechanisms” that Reich argues middle class families used to deal with stagnating incomes included all of the following except:

1. Women move into paid work.
2. Everyone works longer hours.
3. Families stop investing in their children’s education. d. We draw down savings and borrow to the hilt.

## Chapter 20: The Short Run Shapes the Long Run: "Hysteresis"

#### A Fluctuating Natural Rate of Unemployment

Begin our very simple Phillips Curve: 

>π = πe +β(u' −u)

with simple adaptive expectations:

>πe =π−1

But add a difference: the natural rate of unemployment depends on what unemployment was last year:

>u' = (1−θ)u'−1 +θu−1

for some parameter θ between zero and one. 

Suppose that the central bank induces a recession and raises the unemployment rate one percentage point above its natural rate for one year, and then lets unemployment fall back to its natural rate:

1. What is the time path of inflation as a result of this one-year shift in policy? 
2. What is the time path of unemployment?
3. How does the Sacrifice Ratio—the amount of excess point-years of unemployment that must be run in order to permanently reduce the inflation rate by one percent—depend on the parameter θ? 
4. What actions can you think of that the central bank might take that could reduce the value of θ?

#### Supply Shocks

Suppose that a supply shock hits the economy—that is, that for one year the Phillips curve is not:

>π = πe + β(u'− u) 

But is instead:

>π = πe +β(u' − u )+ s

where st is some positive shock to inflation caused by, say, a spike in oil prices. And
suppose that inflation expectations are adaptive:

>πe = π−1

1. What happens to inflation over time if the central bank keeps unemployment at its natural rate always? 
2. What happens to the unemployment rate over time if the central bank adjusts unemployment to keep inflation at its initial value π0 always?

#### Permanent Unemployment Shocks

Suppose we have our standard Phillips curve: 

>π = πe +β(u' − u)

with our standard adaptive inflation expectations: 

>πe =π−1

But that the natural rate of unemployment u' is subject to hysteresis: u' =u−1

How is this situation is different from that of a constant natural rate of unemployment combined with static inflation expectations?

#### The Computer Revolution and the Natural Rate of Unemployment

In the late 1990s Alan Greenspan argued that the natural rate of unemployment in the U.S. had temporarily fallen because of the acceleration of productivity growth. Briefly, outline a model of worker behavior in which this claim of Alan Greenspan’s is true, and outline a model of worker behavior in which this claim of Alan Greenspan’s would have been false. Keep your answer to whatever equations you find necessary and to less than 300 words (and a couple of figures).

#### European Unemployment

Explain—to somebody who has never taken an economics course—the reasons you think that western European unemployment today is so much higher than western European unemployment was back in the 1960s.

#### The Japanese Slowdown

Explain—to somebody who has never taken an economics course—the reasons that you think economic growth in Japan slowed from 4.5% over 1973-1991 to less than 1.5% over 1991-present. Keep your answer to less than 300 words (and a couple of figures).

#### Hysteresis

When economists speak of hysteresis, they refer to the fact that:

1. Once a recession starts, it is likely to last for a while.
2. High unemployment tends to be followed by low unemployment.
3. Prolonged high unemployment can cause the natural rate of unemployment to rise.
4. Prolonged high unemployment will eventually reduce inflation.

## Chapter 21: International Economic Policy

#### Speculative Attacks

Explain—to somebody who has never taken an economics course—why a loss of confidence in the value of a country’s currency on the part of foreign exchange speculators is highly likely to lead to a fall in the rate of investment even if no financial crisis is created. Keep your answer to less than 150 words (and a figure or two).

#### Foreign Monetary Policy

Suppose that many foreign central banks tighten their monetary policies, so that real interest rates abroad rise.

1. How would you expect this change to affect the CF(r) function in the United States? Why?
2. How would the change affect output and the real interest rate in the short run? Explain.
3. How would the change affect net exports, and the real exchange rate in the short run? Explain. 

#### Flexible Price World Foreign Exchange Crises

Start out with our consensus flexible-price model in “difference” form, the relevant parts of which are:

>ΔY = ΔC + ΔI + ΔG + ΔX − ΔIM    
ΔC = Cy x (1−t)(ΔY)  
ΔI = ΔI0 − Ir(Δr)   
ΔX = Xε(Δε)   
Δε = Δε0 − εr(Δr)

and let’s consider the effect of a collapse of confidence in the currency—a large sudden € rise in the Δε0 parameter that governs long-term expectations of the price of foreign currency. 

Suppose that there are no effects on the supply side—ΔY=0—no effects on investor confidence—ΔI0=0—no effects on imports—ΔIM=0—and that government spending is unchanged as well—ΔG=0.

1. In the flexible price model, solve for the equilibrium changes in the exchange rate ε, in the interest rate r, in investment I, and in exports X as a result of the rise in
Δε0.
2. Suppose that the cause of the crisis is that government spending is rising rapidly and that investors have no confidence that the budget will ever be balanced, and thus that the government bonds they own will ever be repaid without inflation. Thus there is a relationship between government spending and the change in expectations of the exchange rate: Δε0 = θΔG for some value of the parameter θ. Now solve for the equilibrium changes in the exchange rate ε, in the interest rate r, in investment I, and in exports X as a result of the rise government spending G.
€
ΔY =ΔC+ΔI+ΔG+ΔX −ΔIM ΔC = Cy (1− t)ΔY
ΔI=ΔI0 −IrΔr−Iε(Δε)2 ΔX = XεΔε
ΔIM = −IMyΔY Δε=Δε0 −εrΔr

#### Sticky Price  Price World Foreign Exchange Crises

Now let’s turn to the consensus sticky-price model, the relevant parts of which are:

>ΔY = ΔC + ΔI + ΔG + ΔX − ΔIM    
ΔC = Cy x (1−t)(ΔY)  
ΔI = ΔI0 − Ir(Δr) - Iε(Δε)^2   
ΔX = Xε(Δε)   
ΔIM = −IMy(ΔY)   
Δε = Δε0 − εr(Δr)

and once again consider the effect of a collapse of confidence in the currency—a large sudden rise in the Δε0 parameter that governs long-term expectations of the price of foreign currency—this time in the short run in which full employment is not guaranteed, and in which the real interest rate r is chosen by the central bank. And not the extra term in the investment equation: a large shift in the exchange rate causes massive bankruptcies, destabilizes the financial system, and causes investment I to collapse and output Y to fall.

1. Solve for the change in the exchange rate as a function of the change in the interest rate r, and then turn that around: if the change in the exchange rate is going to take on a certain value Δε, what must the change in the interest rate Δr be?
2. Now let’s view the central bank as choosing not the interest rate but the exchange rate. In this model, solve for the change in output ΔY as a function of the change in the exchange rate Δε (taking account of the fact that the central bank must choose the change in the interest rate Δr to make the change in the exchange rate equal to the chosen value.
3. What is the best that the central bank can do in the short run. Where should it choose to set the exchange rate and the interest rate (bearing in mind that they are linked) to make the effects of the crisis as small as possible?
4. Suppose that the IMF is on hand to help, and to give the central bank extra foreign exchange R that it can then spend to affect the exchange rate: Δε = Δε0 −εr(Δr) −εr(ΔR). Solve for how the best the central bank can do is affected by the addition of more help from the IMF.

## Chapter 22: Changes in the Macroeconomy and Changes in Macroeconomic Policy

#### Pick the Best Answer

1. If the central bank is targeting the money supply, an increase in government purchases: a. Shifts the LM curve up. b. Shifts the LM curve down. c. Does not affect the LM curve. d. It is not possible to tell.
2. The IS curve slopes down because: a. As the real interest rate rises, the government increases taxes to finance the greater interest payments on its debt. b. As the real interest rate rises, the central bank tightens monetary policy. c. As the real interest rate rises, the government cuts back on its purchases. d. As the real interest rate rises, households invest less in the stock market. e. As the real interest rate rises, firms buy fewer machines and build fewer factories. f. (a) and (b). g. All of the above.
3. Saying that the regression yt = a + bxt + et suffers from omitted variable bias means that: a. There is correlation between the variables left out of the regression (which show up in e) and the variable whose effect on y we are trying to estimate (x). b. The variables left out of the regression (which show up in e) affect the variable whose behavior we are trying to understand (y). c. The researcher chose to omit some observations because they do not support his or her hypothesis. d. y is on average high when x is high, and low when x is low.
4. The following periods are listed in order from least to greatest macroeconomic volatility:va. 1886–1916, 1947–1985, 1985–2005. b. 1886–1916, 1985–2005, 1929–1941. c. 1985–2005, 1947–1985, 1929–1941. d. 1985–2005, 1929–1941, 1947–1985. e. None of the above.

#### The Gold Standard

Label the following statement as True, False, or Uncertain, and explain your answer briefly: “The gold standard played little role in the Great Depression.”

#### Pick the Best Answer

1. Suppose that initially Y > Yf. As the economy moves to long-run equilibrium: a/ Inflation rises. b. Output falls. c. The real interest rate rises. d. (a) and (b). e. All of the above.
2. In the extension of the IS–MP–IA model to include the zero lower bound, the “kink” in the AD curve occurs at: a. The inflation rate given by the IA curve. b. The inflation rate that causes the IS and MP curves to intersect at the “kink” of the MP curve. c. Y = Yf. d. π=0. e. (c) and (d).
3. The fact that inflation has not fallen very much since 2007 despite the fact that unemployment has been very high over that period could be the result of any of the following except: a. Inflation expectations are “anchored.” b. The normal or natural rate of unemployment has risen substantially. c. The Federal Reserve is constrained by the zero lower bound. d. There have been inflation shocks acting to increase the inflation rate.

## Chapter 23: The Past, Present, and Future of Macroeconomics

#### What (briefly!) does Robert Heilbroner think of Karl Marx?

#### What (briefly!) does Robert Heilbroner think of John Maynard Keynes?

## Auxiliary Readings

#### Write one paragraph

(one hundred to two hundred words) explaining to somebody who has not read the article what its main point is: Paul Krugman's "Cartoon Model" http://krugman.blogs.nytimes.com/2008/03/10/a-cartoon-model-of-the-crisis-more-serious-wonkery/

#### Write one paragraph

(one hundred to two hundred words) explaining to somebody who has not read the article what its main point is: Raghuram Rajan, "Global Current Account Imbalances: Hard Landing or Soft Landing?" http://www.imf.org/external/np/speeches/2005/031505.htm

#### Write one paragraph

(one hundred to two hundred words) explaining to somebody who has not read the article what its main point is: Maurice Obstfeld, "Global Imbalances" http://www.econ.berkeley.edu/~obstfeld/280c_sp07/adjustment.pdf

#### Write one paragraph

(one hundred to two hundred words) explaining to somebody who has not read the article what its main point is: Barry Eichengreen,"China's Exchange Rate Regime: The Long and Short of It" http://www.econ.berkeley.edu/~eichengr/research/short.pdf

#### Write one paragraph

(one hundred to two hundred words) explaining to somebody who has not read the article what its main point is: C. Fred Bergsten, "The Dollar and the Renminbi" http://www.iie.com/publications/papers/paper.cfm?ResearchID=747
Institute for International Economics, "China: The Balance Sheet" http://www.petersoninstitute.org/publications/chapters_preview/04648/0

## Essays

1. Why did America have a housing boom in the mid-2000s?

2. Why did the conditions that had been required for mortgage borrowers before 2000--20% down payment, evidence of a stable job, no more than a 33% ratio of housing expenses (including utilities and taxes) to income--disappear in the 2000s?

3. Why did the world economy fall into a very deep economic recession at the end of 2008?

4. Why is recovery from the current downturn in the United States likely to be partial and delayed?

5. Why are the economies of East and South Asia likely to grow much faster than the United States over the next half-decade or so?

6. Why is America’s health care spending per capita so much higher than health care spending in other industrialized countries?

7. What will happen if America never brings its government revenues up to balance with spending, but keeps running federal budget deficits into the future?

## Identifications

1. National product
2. Income-expenditure equation
3. Subprime mortgages
4. Unemployment rate
5. Inflation rate
6. Long-term real risky interest rate
7. Investment-savings curve
8. Investment-savings equation
9. Marginal propensity to consume
10. About how many people lose or quit their jobs in an average month?
11. About how many people get jobs in an average month?
12. About how many people are unemployed in an average month?

## Short Answers

1. Why did America have a housing boom in the mid-2000s?
2. Why did the conditions that had been required for mortgage borrowers before 2000--20% down payment, evidence of a stable job, no more than a 33% ratio of housing expenses (including utilities and taxes) to income-- disappear in the 2000s?
3. Why did the world economy fall into a very deep economic recession at the end of 2008?
4. What are the five (four positive, one negative) major components of national product on the expenditure side?
5. Jean Baptiste Say in 1803 claimed that, because nobody makes anything without intending to use it or sell it, and nobody sells anything without intending to buy something else, that there could be no general shortage of demand in an economy--that there could be a planned excess of supply of some commodities, but it would be balanced by a planned excess of demand of some other commodities. Was he wrong? Why was he wrong?
