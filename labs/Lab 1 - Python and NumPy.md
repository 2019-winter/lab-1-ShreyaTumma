---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.1'
      jupytext_version: 1.2.4
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
---

# Name(s)
Shreya Tumma


**Instructions:** This is an individual assignment, but you may discuss your code with your neighbors.


# Python and NumPy

While other IDEs exist for Python development and for data science related activities, one of the most popular environments is Jupyter Notebooks.

This lab is not intended to teach you everything you will use in this course. Instead, it is designed to give you exposure to some critical components from NumPy that we will rely upon routinely.

## Exercise 0
Please read and reference the following as your progress through this course. 

* [What is the Jupyter Notebook?](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/What%20is%20the%20Jupyter%20Notebook.ipynb#)
* [Notebook Tutorial](https://www.datacamp.com/community/tutorials/tutorial-jupyter-notebook)
* [Notebook Basics](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/Notebook%20Basics.ipynb)

**In the space provided below, what are three things that still remain unclear or need further explanation?**


**YOUR ANSWER HERE**


## Exercises 1-7
For the following exercises please read the Python appendix in the Marsland textbook and answer problems A.1-A.7 in the space provided below.


## Exercise 1

```python
# YOUR SOLUTION HERE
import numpy as np

a = np.full((6,4), 2)
a
```

## Exercise 2

```python
# YOUR SOLUTION HERE
import numpy as np

b = np.ones((6,4))
np.fill_diagonal(b,3)
b
```

## Exercise 3

```python
# YOUR SOLUTION HERE
a*b
```

Why does np.dot(a,b) not work, but the above solution does?
- a * b does element by element multiplication
- dot product does matrix multiplication, and that is not possible in this case because the two arrays do not have compatible dimensions.

    


## Exercise 4

```python
# YOUR SOLUTION HERE
display(np.dot(a.transpose(),b))
np.dot(a,b.transpose())
```

Why are the results different shapes?
- When transposing a rectangular matrix, the shape is changed because the rows become columns and the columns become rows.



## Exercise 5

```python
# YOUR SOLUTION HERE
def pretty_print():
    print('some output')

pretty_print()
```

## Exercise 6

```python
# YOUR SOLUTION HERE
def array_fun():
    
    c = np.random.rand(5,5)
    print(c)
    print("array sum: ",np.sum(c))
    print("array mean: ",np.mean(c))
    print("array min: ",np.min(c))
    print("array max: ",np.max(c))

array_fun()
```

## Exercise 7

```python
# YOUR SOLUTION HERE

def num_occurences_loops():
    f_count = 0
    

    for row in b:
        for item in row:
            if item == 1:
                f_count +=1
    print('Number of ones using loops: ',f_count)

def num_occurences_where():
    w_count = 0
    w_count = np.where(b == 1)
    count = len(w_count[0])
    print('Number of ones using .where(): ',count)

num_occurences_loops()
num_occurences_where()

```

## Excercises 8-???
While the Marsland book avoids using another popular package called Pandas, we will use it at times throughout this course. Please read and study [10 minutes to Pandas](https://pandas.pydata.org/pandas-docs/stable/getting_started/10min.html) before proceeding to any of the exercises below.


## Exercise 8
Repeat exercise A.1 from Marsland, but create a Pandas DataFrame instead of a NumPy array.

```python
# YOUR SOLUTION HERE
import pandas as pd

a = pd.DataFrame(np.ones((6,4)) * 2)
a
```

## Exercise 9
Repeat exercise A.2 using a DataFrame instead.

```python
# YOUR SOLUTION HERE
b = pd.DataFrame(np.ones((6,4)))
np.fill_diagonal(b.values, 3)
b

```

## Exercise 10
Repeat exercise A.3 using DataFrames instead.

```python
# YOUR SOLUTION HERE
a*b
```

Why does np.dot(a,b) not work, but the above solution does?
- a * b does element by element multiplication
- dot product does matrix multiplication, and that is not possible in this case because the two arrays do not have compatible dimensions.


## Exercise 11
Repeat exercise A.7 using a dataframe.

```python
# YOUR SOLUTION HERE
def num_occurences_loops():
    f_count = 0
    #not sure how to solve this part
    for row in range(len(b)):
        for item in b.loc[row]:
            if item == 1:
                f_count+=1
    
    print('Number of ones using loops: ',f_count)

def num_occurences_where():
    w_count = 0
    #w_count = np.where(arr.values == 1)
    w_count = b.where(b.values == 1)
    count = w_count.count().sum()
    print('Number of ones using .where(): ',count)

num_occurences_loops()
num_occurences_where()

```

## Exercises 12-14
Now let's look at a real dataset, and talk about ``.loc``. For this exercise, we will use the popular Titanic dataset from Kaggle. Here is some sample code to read it into a dataframe.

```python
titanic_df = pd.read_csv(
    "https://raw.githubusercontent.com/dlsun/data-science-book/master/data/titanic.csv"
)
titanic_df
```

Notice how we have nice headers and mixed datatypes? That is one of the reasons we might use Pandas. Please refresh your memory by looking at the 10 minutes to Pandas again, but then answer the following.


## Exercise 12
How do you select the ``name`` column without using .iloc?

```python
## YOUR SOLUTION HERE
titanic_df.name
```

## Exercise 13
After setting the index to ``sex``, how do you select all passengers that are ``female``? And how many female passengers are there?

```python
## YOUR SOLUTION HERE
titanic_df.set_index('sex',inplace=True)
titanic_df.loc['female']
```

## Exercise 14
How do you reset the index?

```python
## YOUR SOLUTION HERE
titanic_df.reset_index()
```

```python

```
