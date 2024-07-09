---
title: List and Dictionary Methods
teaching: 40
exercises: 0
---

::::::::::::::::::::::::::::::::::::::: objectives

- Identify and create lists and dictionaries
- Understand the properties and behaviours of lists and dictionaries
- Access values in lists and dictionaries
- Create and access values from nest lists and dictionaries

::::::::::::::::::::::::::::::::::::::::::::::::::

:::::::::::::::::::::::::::::::::::::::: questions

- How can I store many values together?
- How can I create a list succinctly?
- How can I efficiently access nested data?

::::::::::::::::::::::::::::::::::::::::::::::::::

Values can also be stored in other Python data types such as lists, dictionaries,
sets and tuples. Storing objects in a list is a fast and versatile way to apply
transformations across a sequence of values. Storing objects in dictionary as key-value
pairs is useful for extracting specific values i.e. performing lookup operations.

## Create and access lists

Lists have the following properties and behaviours:

- A single list can store different primitive object types and even other lists
- Lists are ordered and have a 0-based index
- Lists can be appended to using the methods `append()` or `insert()`
- Values inside a list can be removed using the methods `remove()` or `pop()`
- Two lists can be concatenated with the operator `+`
- Values inside a list can be conditionally iterated through
- A list is mutable i.e. the values inside a list can be modified in place

To create a list, values are contained within square brackets i.e. `[]` and individually
separated by commas. The function `list()` can also be used to create a list of values
from an iterable object like a string, set or tuple.

```python
# Create a list of integers using []
list_1 = [1, 3, 5, 7]
print(list_1)
```

```output
[1, 3, 5, 7]
```

```python
# Unlike atomic vectors in R, a list can contain multiple primitive object types
list_2 = [1, "one", 1.0, True]
print(list_2)
```

```output
[1, 'one', 1.0, True]
```

```python
# You can also use list() on an iterable object to convert it into a list
string = 'abcdefg'  
list_3 = list(string)  
print(list_3)
```

```output
['a', 'b', 'c', 'd', 'e', 'f', 'g']
```

Because lists have a 0-based index, we can access individual values by their list index
position. For 0-based indexes, the first value always starts at position 0 i.e. the
first element has an index of 0. Accessing multiple values by their index positions
is also referred to as slicing or subsetting a list.

Note that we can use negative numbers as indices in Python. When we do so, the index
`-1` gives us the last element in the list, `-2` gives us the second to last element
in the list, and so on.

```python
# Extract individual values from list_3
print('first value:', list_3[0])
print('second value:', list_3[1])
print('last value:', list_3[-1])
```

```output
first value: a
second value: b
last value: g
```

```python
# A syntax quirk for slicing values is to +1 to the last value's index 
# To extract from index 0 to 2, we need to slice from [0:2+1] or [0:3]

# Extract the first three values from list_3
print('first 3 values:', list_3[0:3])

# Start from index 0 and extract values from each subsequent second position
print('every second value:', list_3[0::2])

# Start from index 1, end at index 3 and extract from each subsequent second position
print('every second value from index 1 to 3:', list_3[1:4:2])
```

```output
first 3 values: ['a', 'b', 'c']
every second value: ['a', 'c', 'e', 'g']
every second value from index 1 to 3: ['b', 'd']
```

## Change list values

Data which can be modified in place is called mutable, while data which cannot be
modified is called immutable. Strings and numbers are immutable in that when we want
to change the value of a string or number variable, we can only replace the old
value with a completely new value.

```python
string = 'abcde'
string[0] = 'b' # Produces a type error as strings are immutable

# TypeError: 'str' object does not support item assignment
```

In contrast, lists are mutable and we can modify them after they have been created.
We can change individual values, append new values, or reorder the whole list through sorting.

```python
list_4 = ['apple', 'pear', 'plum']
print('original list_4:', list_4)

# Change the first value i.e. modify the list in place
list_4[0] = 'banana'
print('modified list_4:', list_4)

# Add new value to list using the method .insert(index number, value)
list_4.insert(1, 'apple') # Index 1 refers to the second position
print('appended list_4:', list_4)
```

```output
original list_4: ['apple', 'pear', 'plum']
modified list_4: ['banana', 'pear', 'plum']
appended list_4: ['banana', 'apple', 'pear', 'plum']
```

```python
# Sorting a list also modifies it in place
list_5 = [2, 1, 3, 7]
list_5.sort()
print('list_5:', list_5)
```

```output
list_5: [1, 2, 3, 7]
```

However, be careful when modifying data in-place. If two variables refer to the same
list, and you modify the list value, it will change for both variables!

```python
# When we assign list_6 to list_5, it means both list_6 and list_5 point to the
# same list object, not that list_6 is a copy of list_5.  

list_6 = list_5  
print('list_5:', list_5)
print('list_6:', list_6)

# Change the first value in list_6 from 1 to 2 
list_6[0] = 2 

print('modified list_6:', list_6)
print('unmodified list_5:', list_5)

# Warning: list_5 and list_6 have both been modified in place!
```

```output
list_5: [1, 2, 3, 7]
list_6: [1, 2, 3, 7]
modified list_6: [2, 2, 3, 7]
unmodified list_5: [2, 2, 3, 7]
```

Because of this behaviour, code which modifies data in place should be handled with care.
You can also avoid this behaviour by expliciting creating a copy of the original list
and modifying only the object copy. This is why creating a copy of the original data
object can be useful in Python.

```python
list_5 = [1, 2, 3, 7]
list_7 = list_5.copy()  
print('list_5:', list_5)
print('list_7:', list_7)

# As list_7 is a completely new object copied from list_5, modifying list_7 does
# not affect list_5.  

list_7[0] = 2 
print('modified list_7:', list_7)
print('unmodified list_5:', list_5)
```

```output
list_5: [1, 2, 3, 7]
list_7: [1, 2, 3, 7]
modified list_7: [2, 2, 3, 7]
unmodified list_5: [1, 2, 3, 7]
```

## Useful list functions

There are a lot of functions and methods which can be applied to lists, such as
`len()`, `max()`, `index()` and so forth. Mathematical operations do not work on lists
of integers, with the exception of `+`.

Note that `+` concatenates two lists into a single longer list, rather than outputting
the sum of two lists of numbers.

```python
list_8 = [1, 2, 3]
list_9 = [4, 5, 6]

list_8 + list_9 # This concatenates the lists and does not sum the two lists together
```

```output
[1, 2, 3, 4, 5, 6]
```

In your spare time after this workshop, you can search for different list functions
and methods and test them out yourselves.

## Nested lists

We have previously mentioned that lists can be used to store other Python object
types, including lists. This means that we can create nested lists in Python i.e.
lists containing lists containing values. This property is useful when we have a
collection of values that we want to access or transform as a subgroup.

To create a nested list, we also use `[]` or `list()` to contain one or more lists of
values of interest.

```python
veg_stock = [
    ['lettuce', 'lettuce', 'tomato', 'zucchini'],
    ['lettuce', 'lettuce', 'carrot', 'zucchini'],
    ['lettuce', 'basil', 'tomato', 'zucchini']
    ]

# Check that veg_stock is a list object
print(type(veg_stock))

# Check that the first value in veg_stock is itself a list
print(veg_stock[0], 'has type', type(veg_stock[0]))  
```

```output
<class 'list'>
['lettuce', 'lettuce', 'tomato', 'zucchini'] has type <class 'list'>
```

To extract the first sub-list within the `veg_stock` list object, we refer to its index
like we would with any other value inside a list i.e. `veg_stock[1]` points to the
second sub-list within the `veg_stock` list.

To access an individual string value inside a sub-list, we make use of a second index,
which points to an individual value inside the sub-list.

```python
print(veg_stock[0]) # Access the first sub-list 
print(veg_stock[0][0]) # Access the first value in the first sub-list 

print(type(veg_stock[0])) # The first value in veg_stock is a list
print(type(veg_stock[0][0])) # The first value in the first list in veg_stock is a string
```

```output
['lettuce', 'lettuce', 'tomato', 'zucchini']
lettuce
<class 'list'>
<class 'str'>
```

In general, however, when we are analysing a large collection of values, the best practice is
to structure those values in columns and rows as a tabular Pandas data frame object.
This is covered in another Carpentries Course called [Python for Social Sciences](https://datacarpentry.org/python-socialsci/08-Pandas.html).

Lists are still incredibly versatile and useful when you have a collection of values that need to
be efficiently accessed or transformed. For example, data frame column names are
commonly extracted and stored inside a list, so that the same transformation can then be
mapped across multiple columns.

## Create and access dictionaries

A dictionary is a Python data type that is particularly suited for enabling quick lookup
operations on unstructured data sets.

A dictionary can therefore be thought of as an unordered list where every item or value
is associated with a unique key (i.e. a self-defined index of unique strings or numbers).
The index values are called keys and a dictionary contains key-value pairs with the
format `{key: value(s)}`.

Dictionaries can be created by listing individual key-values pairs inside `{}` or
using `dict()`.

```python
# A key-value pair can contain single or multiple values  
# Keys are treated as case sensitive and unique
# Multiple values are first stored inside a list  

teams = {
    'data science': ['Mei Ling', 'Paul', 'Gwen', 'Suresh'],
    'user design': ['Amy', 'Linh', 'Sasha'],
    'software dev': ['David', 'Prya'],
    'comms': 'Taylor' 
    } 
```

When using `dict()`, we need to indicate which key is associated with which value.
This can be done directly using tuples, direct association i.e. using `=` or using
`zip()`, which creates a set of tuples from an iterable list.

```python
# To use dict(), key-value pairs are can be stored inside tuples  
ds_emp_status = dict([
        ('Mei Ling', 'full time'),
        ('Paul', 'full time'),
        ('Gwen', 'part time'),
        ('Suresh', 'part time')
    ])  

# Key-value pairs can also be assigned by direct association  
# Keys cannot be strings i.e. wrapped in '' using this approach
ud_emp_status = dict(
    Amy = 'full time',
    Linh = 'full time',
    Sasha = 'casual' 
    ) 

# zip() can also be used if each key has only one value  
sd_emp_status = dict(zip(
    ['David', 'Prya'],
    ['full time', 'full time']
    ))
```

To access a specific value inside a dictionary, we need to specify its key using `[]`.
This is similar to slicing or subsetting a list by specifying its index using `[]`.

```python
# Access the values associated with the key 'data science'
print(teams['data science'])

print('The object teams is of type', type(teams))
print('The dict value', teams['data science'], 'is of type', type(teams['data science']))
```

```output
['Mei Ling', 'Paul', 'Gwen', 'Suresh']
The data object teams is of type <class 'dict'>
The value ['Mei Ling', 'Paul', 'Gwen', 'Suresh'] is of type <class 'list'>
```

We can also access a value from a dictionary using the `get()` method.

```python
print(teams.get('user design'))

# get() also enables us to return an alternate string when the key is not found   
# This prevents our code from returning an error message that halts the analysis

print(teams.get('data engineering', 'WARNING: key does not exist'))
```

```output
['Amy', 'Linh', 'Sasha']
WARNING: key does not exist
```

To access data inside a dictionary, we can also perform the following other actions:

- Check whether a key exists in a dictionary using the keyword `in`
- Retrieve unique dictionary keys using `dict.keys()`
- Retrieve dictionary values using `dict.values()`
- Retrieve dictionary items using `dict.items()`

```python
# Check whether a key exists in a dictionary 
print('data science' in teams) 
print('Data Science' in teams) # Keys are case sensitive  

# Retrieve all dictionary keys  
print(teams.keys())
print(sd_emp_status.keys())

# Retrieve all dictionary values  
print(sd_emp_status.values())  

# Retrieve all dictionary key-value pairs
print(sd_emp_status.items())
```

```output
True
False
dict_keys(['data science', 'user design', 'software dev', 'comms'])
dict_keys(['David', 'Prya'])
dict_values(['full time', 'full time'])
dict_items([('David', 'full time'), ('Prya', 'full time')])
```

To add a new key-value pair to an existing dictionary, we can create a new key and
directly attach a new value to it using `=` or alternatively use the method `update()`.

```python
print('original dict items:', sd_emp_status.items())  

# Add new key-value pair using direct assignment  
sd_emp_status['Mohammad'] = 'full time'

# Add new key-value pair using update({'key': 'value'})   
sd_emp_status.update({'Carrie': 'part time'})

print('updated dict items:', sd_emp_status.items())    
```

```output
original dict items: dict_items([('David', 'full time'), ('Prya', 'full time')])
updated dict items: dict_items([('David', 'full time'), ('Prya', 'full time'), 
('Mohammad', 'full time'), ('Carrie', 'part time')])
```

Because keys are unique, a dictionary cannot contain two keys with the same name. This
means that adding an item using a key that is already present in the dictionary
will cause the previous value to be overwritten.

```python
print('original dict items:', sd_emp_status.items())  

# As the key 'Carrie' already exists, its value will be overwritten
sd_emp_status['Carrie'] = 'full time'
print('updated dict items:', sd_emp_status.items())  
```

```output
original dict items: dict_items([('David', 'full time'), ('Prya', 'full time'), 
('Mohammad', 'full time'), ('Carrie', 'part time')])
updated dict items: dict_items([('David', 'full time'), ('Prya', 'full time'), 
('Mohammad', 'full time'), ('Carrie', 'full time')])
```

To remove a key-value pair for an existing dictionary, we can use the `del` keyword
or the method `pop()`. Using `pop()` also enables us to return an alternate string
if we trt to remove a non-existing key, which prevents our code from returning an
error message that halts the analysis.

```python
print('original dict items:', sd_emp_status.items())

# Delete dictionary keys using del and pop()
del sd_emp_status['Mohammad']
sd_emp_status.pop('Carrie')
sd_emp_status.pop('Anuradha', 'WARNING: key does not exist') # Does not generate an error

print('modified dict items:', sd_emp_status.items())  
```

```output
original dict items: dict_items([('David', 'full time'), ('Prya', 'full time'), 
('Mohammad', 'full time'), ('Carrie', 'full time')])
modified dict items: dict_items([('David', 'full time'), ('Prya', 'full time')])
```

## Nested dictionaries

Similar to lists, dictionaries can be nested as we can also store dictionaries as values
inside a key-value pair using `{}`. Nested dictionaries are useful when we need to
store unstructured data in a complex structure. For example, JSON data is commonly
used for transmitting data in web applications and often exists in a nested structure
that can be stored using nested dictionaries in Python.

```python
# Individual dictionaries are enclosed in {} and separated by a comma
nested_dict = {
    'dict_1': { # First key is a dictionary of key-value pairs 
        'key_1a': 'value_1a',
        'key_1b': 'value_1b'
                },
    'dict_2': { # Second key is another dictionary of key-value pairs
        'key_2a': 'value_2a',
        'key_2b': 'value_2b'
                }
            }

print(nested_dict)
```

```output
{'dict_1': {'key_1a': 'value_1a', 'key_1b': 'value_1b'},
 'dict_2': {'key_2a': 'value_2a', 'key_2b': 'value_2b'}}
```

Similar to working with nested lists, to extract a value from the first sub-dictionary,
we specify both the main dictionary and sub-dictionary keys using `[]`.

```python
# Extract the value for key 2a in dict_2
print('original value:', nested_dict['dict_2']['key_2a'])

# Adding or updating a value can be done through the same approach
nested_dict['dict_2']['key_2a'] = "modified_value_2a"  

print('modified value:', nested_dict['dict_2']['key_2a'])
```

```output
original value: value_2a
modified value: modified_value_2a
```

## Optional: converting lists and dictionaries to Pandas data frames

Lists and dictionaries can be easily converted into a tabular Pandas data frame format.
This can be useful when you need to create a small data set for unit testing purposes.

```python
# Import pandas library
import pandas as pd

# Create a dictionary with each key-value pair representing a data frame column
data = {
    'col_1': [3, 2, 1, 0],
    'col_2': ['a', 'b', 'c', 'd']
    }

df = pd.DataFrame.from_dict(data) 

print(df) # Outputs data as a tabular Pandas data frame   
print(type(df))
```

```output
   col_1 col_2
0      3     a
1      2     b
2      1     c
3      0     d
<class 'pandas.core.frame.DataFrame'>
```



:::::::::::::::::::::::::::::::::::::::: keypoints

- Lists can contain any Python object including other lists
- Lists are ordered i.e. indexed and can therefore be sliced by index number
- Unlike strings and integers, the values inside a list can be modified in place
- A list which contains other lists is referred to as a nested list
- Dictionaries behave like unordered lists and are defined using key-value pairs
- Dictionary keys are unique
- A dictionary which contains other dictionaries is referred to as a nested dictionary
- Values inside nested lists and dictionaries can be accessed by an additional index

::::::::::::::::::::::::::::::::::::::::::::::::::


