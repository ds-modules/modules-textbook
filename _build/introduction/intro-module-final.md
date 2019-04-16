---
interact_link: content/introduction/intro-module-final.ipynb
kernel_name: conda-root-py
title: 'Intro to Python and Jupyter'
prev_page:
  url: /introduction/ds-intro
  title: 'Data Science in Python and Jupyter'
next_page:
  url: /features/notebooks
  title: 'Jupyter notebooks'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---

# Introduction to Data Science
---

Welcome to Data Science! In this notebook, you will learn how to use Jupyter Notebooks and the basics of programming in Python.

*Estimated Time: 30 minutes*

---

**Topics Covered:**
- Learn how to work with Jupyter notebooks.
- Learn about variables in Python, including variable types, variable assignment, and arithmetic.
- Learn about functions in Python, including defining and calling functions, as well as scope.

**Parts:**
- Jupyter Notebooks
- Programming in Python
- Variables
- Functions
- Scope

## Jupyter Notebooks
---
In this section, we will learn the basics of how to work with Jupyter notebooks.

This Jupyter notebook is composed of 2 kinds of cells: markdown and code. A **markdown cell**, such as this one, contains text. A **code cell** contains code in Python, a programming language that we will be using for the remainder of this module.

To run a code cell, press Shift-Enter or click Cell > Run Cells in the menu at the top of the screen. To edit a code cell, simply click in the cell and make your changes.

### Exercise

Try running the code below. What happens?



{:.input_area}
```python
# CODE
print("Hello World!")
```


{:.output .output_stream}
```
Hello World!

```

Now, let's try editing the code. In the cell below, replace "friend" with your name for a more personalized message.



{:.input_area}
```python
print("Welcome to Jupyter notebooks, friend.")
```


{:.output .output_stream}
```
Welcome to Jupyter notebooks, friend.

```

## Programming in Python
---
Now that you are comfortable with using Jupyter notebooks, we can learn more about programming in this notebook.

### What is Programming?
**Programming** is giving the computer a set of step-by-step instructions to follow in order to execute a task. It's a lot like writing your own recipe book! For example, let's say you wanted to teach someone how to make a PB&J sandwich:
1. Gather bread, peanut butter, jelly, and a spreading knife.
2. Take out two slices of bread.
3. Use the knife to spread peanut butter on one slice of bread.
4. Use the knife to spread jelly on the other slice of bread.
5. Put the two slices of bread together to make a sandwich.

Just like that, programming is breaking up a complex task into smaller commands for the computer to understand and execute.

In order to communicate with computers, however, we must talk to them in a way that they can understand us: via a **programming language**. 

There are many different kinds of programming languages, but we will be using **Python** because it is concise, simple to read, and applicable in a variety of projects - from web development to mobile apps to data analysis.

## Variables
---

In programming, we often compute many values that we want to save so that we can use the result in a later step. For example, let's say that we want to find the number of seconds in a day. We can easily calculate this with the following:

<p style="text-align: center">$60 * 60 * 24 = 86400$ seconds</p> 

However, let's say that your friend Alexander asked you how many seconds there are in three days. We could, of course, perform the calculation in a similar manner:

<p style="text-align: center">$(60 * 60 * 24) * 3 = 259200$ seconds</p> 

But we see that we repeated the calculation in parentheses above. Instead of doing this calculation again, we could have saved the result from our first step (calculating the number of seconds in a day) as a variable.



{:.input_area}
```python
# This is Python code that assigns variables.
# The name to the left of the equals sign is the variable name.
# The value to the right of the equals sign is the value of the variable.
# Press Shift-Enter to run the code and see the value of our variable!

seconds_in_day = 60 * 60 * 24 # This is equal to 86400.
seconds_in_day
```





{:.output .output_data_text}
```
86400
```



Then, we can simply multiply this variable by three to get the number of seconds in *three* days:



{:.input_area}
```python
# The code below takes the number of seconds in a day (which we calculated in the previous code cell)
# and multiplies it by 3 to find the number of seconds in 3 days.

seconds_in_three_days = seconds_in_day * 3  # This is equal to 259200.
seconds_in_three_days
```





{:.output .output_data_text}
```
259200
```



As you can see, variables can be used to simplify calculations, make code more readable, and allow for repetition and reusability of code. 

### Variable Types

Next, we'll talk about a few types of variables that you'll be using. As we saw in the example above, one common type of variable is the *integer* (positive and negative whole numbers). You'll also be using decimal numbers in Python, which are called *doubles* (positive and negative decimal numbers). 

A third type of variable used frequently in Python is the *string*; strings are essentially sequences of characters, and you can think of them as words or sentences. We denote strings by surrounding the desired value with quotes. For example, "Data Science" and "2017" are strings, while `bears` and `2020` (both without quotes) are not strings.

Finally, the last variable type we'll go over is the *boolean*. They can take on one of two values: `True` or `False`. Booleans are often used to check conditions; for example, we might have a list of dogs, and we want to sort them into small dogs and large dogs. One way we could accomplish this is to say either `True` or `False` for each dog after seeing if the dog weighs more than 15 pounds. 

Here is a table that summarizes the information in this section:

|Variable Type|Definition|Examples|
|-|-|-|
|Integer|Positive and negative whole numbers|`42`, `-10`, `0`|
|Double|Positive and negative decimal numbers|`73.9`, `2.4`, `0.0`|
|String|Sequence of characters|`"Go Bears!"`, `"variables"`|
|Boolean|True or false value|`True`, `False`|


### Arithmetic
Now that we've discussed what types of variables we can use, let's talk about how we can combine them together. As we saw at the beginning of this section, we can do basic math in Python. Here is a table that shows how to write such operations:

|Operation|Operator|Example|Value|
|-|-|-|
|Addition|+|`2 + 3`|`5`|
|Subtraction|-|`2 - 3`|`-1`|
|Multiplication|*|`2 * 3`|`6`|
|Division|/|`7 / 3`|`2.66667`|
|Remainder|%|`7 % 3`|`1`|
|Exponentiation|**|`2 ** 0.5`|`1.41421`|

In addition, you can use parentheses to denote priority, just like in math.

As an exercise, try to predict what each of these lines below will print out. Then, run the cell and check your answers.



{:.input_area}
```python
q_1 = (3 + 4) / 2
print(q_1) # What prints here?

q_2 = 3 + 4 / 2
print(q_2) # What prints here?

some_variable = 1 + 2 + 3 + 4 + 5
q_3 = some_variable * 4
print(q_3) # What prints here?

q_4 = some_variable % 3
print(q_4) # What prints here?

step_1 = 6 * 5 - (6 * 3)
step_2 = (2 ** 3) / 4 * 7
q_5 = 1 + step_1 ** 2 * step_2
print(q_5) # What prints here?
```


{:.output .output_stream}
```
3.5
5.0
60
0
2017.0

```

## Functions

So far, you've learnt how to carry out basic operations on your inputs and assign variables to certain values.
Now, let's try to be more efficient. 

Let's say we want to perform a certain operation on many different inputs that will produce distinct outputs. What do we do? We write a _**function**_.

A function is a block of code which works a lot like a machine: it takes an input, does something to it, and produces an output. 

The input is put between brackets and can also be called the _argument_ or _parameter_. Functions can have multiple arguments.

Try running the cell below after changing the variable _name_:




{:.input_area}
```python
# Edit this cell to your own name!
name = "John Doe"

# Our function
def hello(name):
    return "Hello " + name + "!"

hello(name)
```


Interesting, right? Now, you don't need to write 10 different lines with 10 different names to print a special greeting for each person. All you need to is write one function that does all the work for you!

Functions are very useful in programming because they help you write shorter and more modular code. A good example to think of is the _print_ function, which we've used quite a lot in this module. It takes many different inputs and performs the specified task, printing its input, in a simple manner.

Now, let's write our own function. Let's look at the following rules: 

### Defining
- All functions must start with the "def" keyword.  
- All functions must have a name, followed by parentheses, followed by a colon. Eg. def hello( ):
- The brackets may have a variable that stores its arguments (inputs)
- All functions must have a "return" statement which will return the output. Think of a function like a machine. When you put something inside, you want it to return something. Hence, this is very important.

### Calling
After you define a function, it's time to use it. This is known as _calling_ a function. 

To call a function, simply write the name of the function with your input variable in brackets (argument).




{:.input_area}
```python
# Complete this function
def #name(argument):
    return # function must return a value

# Calling our function below...
my_first_function(name)
```


Great! Now let's do some math. Let's write a function that returns the square of the input.

Try writing it from scratch!



{:.input_area}
```python
# square function 


square(5)
```


Neat stuff! Try different inputs and check if you get the correct answer each time.

You've successfully written your first function from scratch! Let's take this up one notch.

#### The power function

_pow_ is a function that takes in two numbers: x, which is the "base" and y, the "power". So when you write pow(3,2) the function returns 3 raised to the power 2, which is 3^2 = 9. 

Task: Write a function called _mulpowply_ which takes in three inputs (x, y, z) and returns the value of x multiplied by y to power z. Symbolically, it should return (xy)^z.



{:.input_area}
```python
# mulpowply function


```


## Scope
---
Programming is great, but it can also be quite peculiar sometimes. For example, each variable defined outside of any functions by default, is **global**. 

Try executing the code below:



{:.input_area}
```python
# Global Variable - name
name = "Harry Potter"

# our function
def salutation(name):
    return "Hi " + name + ", nice to meet you!"

# calling our function
salutation(name)

# un-comment the line below
#salutation("Roonald Wazlib")
```


Even though your argument was called _name_, it didnt output Harry Potter, which was the **global** value of the variable called name. Instead, it gave preference to the **local** value which was given to the function as an argument, Roonald Wazlib. 

Think of it as filling your coffeemaker (function) up with coffee (variable). If you have a variable with **global** access called _name_ which is filled with coffee called Harry Potter, you can choose to either:

1) Not input another value in your function. (Use the same name of the **global** variable as your argument)

In this case, the **global** type of coffee will still be used. 

2) Choose to fill another value. In this case, your function will assign the value you pass as the argument to the “variable” which **is** the argument.

Think of it as overriding your **global** coffee and putting a new type of coffee into your coffeemaker.

### Activity

Using the rules of scope you've learned so far, complete the function _puzzle_ to output the value **35**.



{:.input_area}
```python
# Scope Puzzle!
x = 5
y = 6
z = 7

def puzzle(x, y):
    return x * y

# fill in this function call
puzzle()

```


## Control
---
Sometimes, we want to manipulate the flow of our code. For example, we might want our code to make decisions on its own or repeat itself a certain amount of times. By implementing control structures, we can avoid redundant code and make processes more efficient.

### Conditionals
We use **conditionals** to run certain pieces of code _if_ something is true. For example, we should only go to the grocery store _if_ we are out of peanut butter!

We use **comparators** to determine whether an expression is _true_ or _false_. There are six comparators to be aware of:
1. Equal to: ==
2. Not equal to: !=
3. Greater than: >
4. Greater than or equal to: >=
5. Less than: <
6. Less than or equal to: <=

Let's try it out!



{:.input_area}
```python
# EXERCISE 1
# Determine whether the following will print true or false
# Run the code to check your answers!

print(10 == 10)

print(2016 < 2017)

print("foo" != "bar")

print( (1+2+3+4+5) <=  (1*2*3))
```




{:.input_area}
```python
# EXERCISE 2

# Write an expression that evaluates to True
expression1 = # YOUR CODE HERE

# Write an expression that evaluates to False
expression2 = # YOUR CODE HERE

print(expression1)
print(expression2)
```


Now that we know how to compare values, we can tell our computer to make decisions using the **if statement**.

### If Statements
An **if statement** takes the following form:



{:.input_area}
```python
# Please do not run this code, as it will error. It is provided as a skeleton.

if (condition1):
    # code to be executed if condition1 is true
elif (condition2):
    # code to be executed if condition2 is true
else:
    # code to be executed otherwise
```


With if statements, we can control which code is executed. Check out how handy this can be in the activity below!



{:.input_area}
```python
# We want to make a PB&J sandwich, but things keep going wrong!

# Modify the variables below so that you go grocery shopping 
# with no mishaps and successfully purchase some peanut butter.

# Run the code when you're done to see the results.

print("Let's make a PB&J sandwich!")
peanut_butter = 10
jelly = 100
gas = 60
flat_tire = True

if (peanut_butter < 50):
    print("Uh oh! We need more peanut butter. Must go grocery shopping...")
    if (gas < 75):
        print("Oops! Your car is out of gas :(")
    elif (flat_tire):
        print("Oh no! You have a flat tire :'(")
    else:
        print("You made it to the grocery store and succesfully got peanut butter!")
        peanut_butter = # reset the value of peanut_butter so it is 100% full again
else:
    print("We have all the ingredients we need! Yummy yummy yay!")
```


### For Loops
We can also regulate the flow of our code by repeating some action over and over. Say that we wanted to greet ten people. Instead of copying and pasting the same call to _print_ over and over again, it would be better to use a **for loop**.

A basic **for loop** is written in the following order:
- The word "for"
- A name we want to give each item in a sequence
- The word "in"
- A sequence (i.e. "range(100)" to go through numbers 0-99

For example, to greet someone ten times, we could write:



{:.input_area}
```python
# Run me to see "hello!" printed ten times!
for i in range(10):
    print("hello!")
```


In this way, for loops help us avoid redundant code and have useful capabilities.

**Exercise:** Write a function that returns the sum of the first _n_ numbers, where _n_ is the input to the function. Use a for loop!



{:.input_area}
```python
def sum_first_n(n):
    # YOUR CODE HERE

sum_first_n(5) # should return 1+2+3+4+5 = 15
```


## Conclusion
---
Congratulations! You've successfully learnt the basics of programming: creating your own variables, writing your own functions, and controlling the flow of your code! You will apply the concepts learnt throughout this notebook in class. After delving into this notebook, you are only just getting started!

---

## Bibliography

Some examples adapted from the UC Berkeley Data 8 textbook, <a href="https://www.inferentialthinking.com">*Inferential Thinking*</a>.

Authors:
- Shriya Vohra
- Scott Lee
- Pancham Yadav
