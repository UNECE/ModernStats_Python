---
title: "Introduction"
teaching: 15
exercises: 0
questions:
- "What is programming?"
- "How do I document code?"
- "How do I find reliable and safe resources or code online?"
objectives:
- "identify basic concepts in programming"
keypoints:
- Python is an interpreted language.  
- Code is commonly developed inside an integrated development environment. 
- A typical Python workflow uses base Python and additional Python packages developed for statistical programming purposes. 
- In-line and external documentation helps ensure that your code is readable.  
- You can find help through the built-in help function and external resources. 
---

## Programming in Python

In most general terms, programming is the process of writing instructions for a computer. In this course we will be using Python as the language to communicate with the computer. 

> Strictly speaking, Python is an interpreted language, rather than a compiled language, meaning we are not communicating directly with the computer when we use Python. When we run Python code, our Python source code is first translated into byte code, which is then executed by the Python virtual machine. 

Programming is a wide topic including a variety of techniques and tools. In this course we'll be focusing on programming for statistical analysis.


### IDEs

IDE stands for Integrated Development Environment. IDEs are where you will write, edit, and debug python scripts, so you want to choose one that makes you feel comfortable and includes the functionality that you need. Some open-source IDEs for Python include [JupyterLab](https://jupyter.org/) and [Visual Studio Code](https://code.visualstudio.com/docs/languages/python). 

### Packages

Packages, or libraries, are extensions to the statistical programming language. They contain code, data, and documentation in a standardised collection format that can be installed by users, typically via a centralised software repository. A typical Python workflow will use base Python (the core operations and functions provided by your Python installation) as well as specialised data analysis and scientific packages like [NumPy](https://numpy.org/), [SciPy](https://scipy.org/) and [Pandas](https://pandas.pydata.org/).   

## Best Practices

Let's overview some base concepts that any programmer should always keep in mind.

### Documentation

Have you ever returned to a task and tried to read a note that you quickly scrawled for yourself the last time you were working on it? Have you ever inherited a project from a colleague and found you have no idea what remains to be done?

It can be very challenging to return to your own work or a colleague's and this goes doubly for programming. Documentation is one way we can reduce the burden on future selves and our colleagues.

#### Inline Documentation

As a new programmer, inline documentation can be the most helpful. Inline documentation refers to writing comments on the same line as your code. For example, if we wrote a line of code to sum 1+1, we might document it as follows:

~~~
1+1         # adding the numbers 1 and 1 together.
~~~
{: .language-python}

Although this is a very simple line of code and it might seem like overkill to document it in this way, these types of comments can be very helpful in jogging your memory when returning to a project. Inline comments can also help you to break multi-step programs into digestible and readable pieces.

#### External Documentation
Sometimes you require more detail than you can comfortably fit in your inline documentation. In this case it can be helpful to create separate files to document your project. This type of documentation will typically focus on the goals, scope, and any special instructions relating to your project rather than the details fo your code. The most common type of external documentation is a README file. It is best practice to create a basic README file for any project. A basic README should include:
- a brief description of the project,
- any special instructions for installation or use,
- the authors and any references.

README files are just text files and it is best practice is to save your README file as a `README.md` markdown document. This file format is automatically recognised by code repositories like GitHub, so your README contents are displayed alongside your code repository. 
#### DocStrings

In [chapter 7: functions](/_episodes/07-functions.md) we'll learn about documentation specific to functions known as DocStrings.

## Getting Help
Later on, in [chapter 10: Errors and Exceptions](/_episodes/10-errors_exceptions.md) we will cover errors in more detail. However, before we get there it's very likely you'll need some assistance writing Python code.

### Built-in Help

There is a [help function](https://docs.python.org/3/library/functions.html#help) built into base Python. You can use it to investigate built-in functions, data types, and more. For example, say we want to know more about the print() function in Python:

~~~
help(print)
~~~
{: .language-python}

~~~
Help on built-in function print in module builtins:

print(...)
    print(value, ..., sep=' ', end='\n', file=sys.stdout, flush=False)

    Prints the values to a stream, or to sys.stdout by default.
    Optional keyword arguments:
    file:  a file-like object (stream); defaults to the current sys.stdout.
    sep:   string inserted between values, default a space.
    end:   string appended after the last value, default a newline.
-- More  --
~~~
{: .output}

### Finding Resources online

[Stack Overflow](https://stackoverflow.com/) is a valuable resource for programmers of all levels. It can be daunting to post your own question! Fortunately, chances are someone else has already asked a similar question! 

[The Official Python Documentation](https://www.python.org/) is another great resource.

It can also be helpful to do a general search for a particular topic or error message. It's very likely the first few results will be from StackOverflow, followed by a few from official documentation and then you may start seeing results from personal blogs or third parties. These third party results can sometime be valuable but we should be cautious! Here are a few things to keep in mind when you are looking for online resources:
1. Don't download or install anything unless you are certain of what it is and why you need it.
2. Don't copy or run code unless you fully understand what it does.
3. Python is an open-source language; official documentation and resources will not be behind a paywall.
4. You may not find a resource or solution to fit your exact needs. Try to be flexible and adapt online solutions to fit your needs.






{% include links.md %}

