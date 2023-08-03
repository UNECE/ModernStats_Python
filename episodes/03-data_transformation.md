---
title: Data Transformation
teaching: 40
exercises: 20
---

::::::::::::::::::::::::::::::::::::::: objectives

- Explain what a library is and what libraries are used for.
- Import a Python library and use the functions it contains.
- Read tabular data from a file into a program.
- Select individual values and subsections from data.
- Perform operations on arrays of data.

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- How can I process tabular data files in Python?

::::::::::::::::::::::::::::::::::::::::::::::::::

Words are useful, but what's more useful are the sentences and stories we build with them.
Similarly, while a lot of powerful, general tools are built into Python,
specialized tools built up from these basic units live in
[libraries](../learners/reference.md#library)
that can be called upon when needed.

## Loading data into Python

To begin processing the clinical trial inflammation data, we need to load it into Python. Python can work with many different file types. Text files can be loaded into Python by using the base Python function
```python
Open("filename.txt", "r") 
```
where "r" means read only, or if you want to write to the file, you can use "w". 

However, our patient data is in a csv. file, which is more commonly loaded by using a library. Python has hundreds of thousands of libraries to choose from to help carry out your work. Importing a library is like getting a piece of lab equipment out of a storage locker and setting it
up on the bench. Libraries provide additional functionality to the basic Python package, much like
a new piece of equipment adds functionality to a lab space. Just like in the lab, importing too
many libraries can sometimes complicate and slow down your programs - so we only import what we
need for each program. There are a couple common Python libraries to load (and work with data). 

## pandas

The first library we will present is called [pandas](https://pandas.pydata.org/docs/index.html) pandas is a Python library containing a set of functions and specialised data structures that have been designed to help Python programmers to perform data analysis tasks in a structured way.

Most of the things that pandas can do can be done with basic Python, but the collected set of pandas functions and data structure makes the data analysis tasks more consistent in terms of syntax and therefore aids readabilty.

Remember to write the library name with a lower case 'p' because the name of the package and Python is case sensitive.

### Importing the pandas library

Importing the pandas library is done in exactly the same way as for any other library. In almost all examples of Python code using the pandas library, it will have been imported and given an alias of `pd`. We will follow the same convention.

```python
import pandas as pd
```

### Pandas data structures

There are two main data structure used by pandas, they are the Series and the Dataframe. The Series equates in general to a vector or a list. The Dataframe is equivalent to a table. Each column in a pandas Dataframe is a pandas Series data structure.

We will mainly be looking at the Dataframe.

We can easily create a Pandas Dataframe by reading a .csv file

### Reading a csv file

When we read a csv dataset in base Python we did so by opening the dataset, reading and processing a record at a time and then closing the dataset after we had read the last record. Reading datasets in this way is slow and places all of the responsibility for extracting individual data items of information from the records on the programmer.

The main advantage of this approach, however, is that you only have to store one dataset record in memory at a time. This means that if you have the time, you can process datasets of any size.

In Pandas, csv files are read as complete datasets. You do not have to explicitly open and close the dataset. All of the dataset records are assembled into a Dataframe. If your dataset has column headers in the first record then these can be used as the Dataframe column names. You can explicitly state this in the parameters to the call, but pandas is usually able to infer that there ia a header row and use it automatically.

To tell Python that we'd like to start using pandas, we need to [import](../learners/reference.md#import) it: 

```python
import pandas as pd
```
Often, libraries are given an alias or a short form name, in this case pandas is given the alias "pd". Aliases for common data analysis libraries include:

```python
import pandas as pd
import numpy as np
import matplotlib as plt
import seaborn as sns
```
Once we've imported the library, we can ask the library to read our data file for us:

```python
pd.read_csv("filename.csv)
```
pandas is a commonly used library for working with and analysing data. However, we will be working with a different package for the remainder of this course. If you would like to learn more about data manipulation and analysis using pandas, we recommend checking out [Data Analysis and Visualization with Python for Social Scientists](https://datacarpentry.org/python-socialsci/).

## numpy

The second package that we will present is called
[NumPy](https://numpy.org/doc/stable "NumPy Documentation"), which stands for Numerical Python. 
In general, you should use this library when you want to do fancy things with lots of numbers,
especially if you have matrices or arrays. Numpy matrices are typically lighter weight with better performance, particularly when working with large datasets. 

We will be using this package to work with our clinical trial inflammation data. 

To tell Python that we'd like to start using NumPy,
we need to [import](../learners/reference.md#import) it:

```python
import numpy as np
```
Now that we have imported the library, we can ask the library (by using the alisa np) to read our data file for us:

```python
np.loadtxt(fname='inflammation-01.csv', delimiter=',')
```

```output
array([[ 0.,  0.,  1., ...,  3.,  0.,  0.],
       [ 0.,  1.,  2., ...,  1.,  0.,  1.],
       [ 0.,  1.,  1., ...,  2.,  1.,  1.],
       ...,
       [ 0.,  1.,  1., ...,  1.,  1.,  1.],
       [ 0.,  0.,  0., ...,  0.,  2.,  0.],
       [ 0.,  0.,  1., ...,  1.,  1.,  0.]])
```

The expression `np.loadtxt(...)` is a
[function call](../learners/reference.md#function-call)
that asks Python to run the [function](../learners/reference.md#function) `loadtxt` which
belongs to the `np` library.
The dot notation in Python is used most of all as an object attribute/property specifier or for invoking its method. `object.property` will give you the object.property value,
`object_name.method()` will invoke on object\_name method.

As an example, John Smith is the John that belongs to the Smith family.
We could use the dot notation to write his name `smith.john`,
just as `loadtxt` is a function that belongs to the `np` library.

`np.loadtxt` has two [parameters](../learners/reference.md#parameter): the name of the file
we want to read and the [delimiter](../learners/reference.md#delimiter) that separates values
on a line. These both need to be character strings
(or [strings](../learners/reference.md#string) for short), so we put them in quotes.

Since we haven't told it to do anything else with the function's output,
the [notebook](../learners/reference.md#notebook) displays it.
In this case,
that output is the data we just loaded.
By default,
only a few rows and columns are shown
(with `...` to omit elements when displaying big arrays).
Note that, to save space when displaying NumPy arrays, Python does not show us trailing zeros,
so `1.0` becomes `1.`.

Our call to `np.loadtxt` read our file
but didn't save the data in memory.
To do that,
we need to assign the array to a variable. In a similar manner to how we assign a single
value to a variable, we can also assign an array of values to a variable using the same syntax.
Let's re-run `np.loadtxt` and save the returned data:

```python
data = np.loadtxt(fname='inflammation-01.csv', delimiter=',')
```

This statement doesn't produce any output because we've assigned the output to the variable `data`.
If we want to check that the data have been loaded,
we can print the variable's value:

```python
print(data)
```

```output
[[ 0.  0.  1. ...,  3.  0.  0.]
 [ 0.  1.  2. ...,  1.  0.  1.]
 [ 0.  1.  1. ...,  2.  1.  1.]
 ...,
 [ 0.  1.  1. ...,  1.  1.  1.]
 [ 0.  0.  0. ...,  0.  2.  0.]
 [ 0.  0.  1. ...,  1.  1.  0.]]
```

Now that the data are in memory,
we can manipulate them.
First,
let's ask what [type](../learners/reference.md#type) of thing `data` refers to:

```python
print(type(data))
```

```output
<class 'np.ndarray'>
```

The output tells us that `data` currently refers to
an N-dimensional array, the functionality for which is provided by the NumPy library.
These data correspond to arthritis patients' inflammation.
The rows are the individual patients, and the columns
are their daily inflammation measurements.

:::::::::::::::::::::::::::::::::::::::::  callout

### Data Type

A Numpy array contains one or more elements
of the same type. The `type` function will only tell you that
a variable is a NumPy array but won't tell you the type of
thing inside the array.
We can find out the type
of the data contained in the NumPy array.

```python
print(data.dtype)
```

```output
float64
```

This tells us that the NumPy array's elements are
[floating-point numbers](../learners/reference.md#floating-point-number).


::::::::::::::::::::::::::::::::::::::::::::::::::

With the following command, we can see the array's [shape](../learners/reference.md#shape):

```python
print(data.shape)
```

```output
(60, 40)
```

The output tells us that the `data` array variable contains 60 rows and 40 columns. When we
created the variable `data` to store our arthritis data, we did not only create the array; we also
created information about the array, called [members](../learners/reference.md#member) or
attributes. This extra information describes `data` in the same way an adjective describes a noun.
`data.shape` is an attribute of `data` which describes the dimensions of `data`. We use the same
dotted notation for the attributes of variables that we use for the functions in libraries because
they have the same part-and-whole relationship.

If we want to get a single number from the array, we must provide an
[index](../learners/reference.md#index) in square brackets after the variable name, just as we
do in math when referring to an element of a matrix.  Our inflammation data has two dimensions, so
we will need to use two indices to refer to one specific value:

```python
print('first value in data:', data[0, 0])
```

```output
first value in data: 0.0
```

```python
print('middle value in data:', data[29, 19])
```

```output
middle value in data: 16.0
```

The expression `data[29, 19]` accesses the element at row 30, column 20. While this expression may
not surprise you,
`data[0, 0]` might.
Programming languages like Fortran, MATLAB and R start counting at 1
because that's what human beings have done for thousands of years.
Languages in the C family (including C++, Java, Perl, and Python) count from 0
because it represents an offset from the first value in the array (the second
value is offset by one index from the first value). This is closer to the way
that computers represent arrays (if you are interested in the historical
reasons behind counting indices from zero, you can read
[Mike Hoye's blog post](https://exple.tive.org/blarg/2013/10/22/citation-needed/)).
As a result,
if we have an M×N array in Python,
its indices go from 0 to M-1 on the first axis
and 0 to N-1 on the second.
It takes a bit of getting used to,
but one way to remember the rule is that
the index is how many steps we have to take from the start to get the item we want.

![](fig/python-zero-index.svg){alt="'data' is a 3 by 3 numpy array containing row 0: \['A', 'B', 'C'\], row 1: \['D', 'E', 'F'\], androw 2: \['G', 'H', 'I'\]. Starting in the upper left hand corner, data\[0, 0\] = 'A', data\[0, 1\] = 'B',data\[0, 2\] = 'C', data\[1, 0\] = 'D', data\[1, 1\] = 'E', data\[1, 2\] = 'F', data\[2, 0\] = 'G',data\[2, 1\] = 'H', and data\[2, 2\] = 'I',in the bottom right hand corner."}

:::::::::::::::::::::::::::::::::::::::::  callout

## In the Corner

What may also surprise you is that when Python displays an array,
it shows the element with index `[0, 0]` in the upper left corner
rather than the lower left.
This is consistent with the way mathematicians draw matrices
but different from the Cartesian coordinates.
The indices are (row, column) instead of (column, row) for the same reason,
which can be confusing when plotting data.


::::::::::::::::::::::::::::::::::::::::::::::::::

## Slicing data

An index like `[30, 20]` selects a single element of an array,
but we can select whole sections as well.
For example,
we can select the first ten days (columns) of values
for the first four patients (rows) like this:

```python
print(data[0:4, 0:10])
```

```output
[[ 0.  0.  1.  3.  1.  2.  4.  7.  8.  3.]
 [ 0.  1.  2.  1.  2.  1.  3.  2.  2.  6.]
 [ 0.  1.  1.  3.  3.  2.  6.  2.  5.  9.]
 [ 0.  0.  2.  0.  4.  2.  2.  1.  6.  7.]]
```

The [slice](../learners/reference.md#slice) `0:4` means, "Start at index 0 and go up to,
but not including, index 4". Again, the up-to-but-not-including takes a bit of getting used to,
but the rule is that the difference between the upper and lower bounds is the number of values in
the slice.

We don't have to start slices at 0:

```python
print(data[5:10, 0:10])
```

```output
[[ 0.  0.  1.  2.  2.  4.  2.  1.  6.  4.]
 [ 0.  0.  2.  2.  4.  2.  2.  5.  5.  8.]
 [ 0.  0.  1.  2.  3.  1.  2.  3.  5.  3.]
 [ 0.  0.  0.  3.  1.  5.  6.  5.  5.  8.]
 [ 0.  1.  1.  2.  1.  3.  5.  3.  5.  8.]]
```

We also don't have to include the upper and lower bound on the slice.  If we don't include the lower
bound, Python uses 0 by default; if we don't include the upper, the slice runs to the end of the
axis, and if we don't include either (i.e., if we use ':' on its own), the slice includes
everything:

```python
small = data[:3, 36:]
print('small is:')
print(small)
```

The above example selects rows 0 through 2 and columns 36 through to the end of the array.

```output
small is:
[[ 2.  3.  0.  0.]
 [ 1.  1.  0.  1.]
 [ 2.  2.  1.  1.]]
```


::::::::::::::::::::::::::::::::::::::::::::::::::

