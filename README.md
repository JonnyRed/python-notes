# Python notes

This README contains some notes on how to use Python for various tasks,
such as:

* Testing code with doctest, a module that allows you to write tests
as part of the documentation.
* Choosing a license for your project, with a link to a resource that
helps you compare different options.
* Creating a gitignore file, with a link to a template for Python
projects.
* Formatting strings with the .format() method, which lets you insert
and format values in strings.
* The README also includes some examples of code and output, using
the Python console and doctest. Some parts of the output are skipped
or elided for brevity, using doctest directives.

# Doctest

To test the code in this README run the following python script

```bash
python -m doctest README.md  -v
```

Ellipsis in doctests

Whenever possible, I extracted the Python console listings in this book
from doctest to ensure accuracy. When the output was too long, the
elided part is marked by an ellipsis (...)

* `doctest: +[ELLIPSIS]` directive to make the doctest pass,
used in exceptions see [ELLIPSIS][doctest ellipsis]

* `doctest: +SKIP` directive to make the doctest pass. Used as
documentation aid see [SKIP][docktest skip]

# Licenses

[choosealicense.com][Choose a License] is a good resource

# gitignore

The python gitignore file is from [python gitignore][git python ignore]

# format strings

Sure. The Python string `.format()` method is a powerful tool for
formatting strings. It can be used to insert variables, expressions,
and other values into strings, and it can also be used to control
the formatting of the output.

The .format() method takes two types of arguments:
* Positional arguments
    * are inserted into the template string in the order that they are
    specified
* Keyword arguments
    * are inserted into the template string by name.

* The replacement fields in the template string are enclosed in curly
braces ({})
* Anything not contained in curly braces is literal text that's copied
directly from the template to the output.

The `.format()` method supports a variety of formatting options, such as:
* Aligning text to the left, right, or center of the output.
* Specifying the width and precision of numbers.
* Using different formatting styles for different types of data.

The `.format()` method is a versatile and powerful tool for
formatting strings. It can be used to create formatted output that
is both readable and easy to understand.

__Inserting variables:__

```python

>>> name, age = 'John Doe', 30
>>> formatted_string = (
...    'My name is {name} and I am {age} years old.'
...    .format(name=name, age=age)
... )
>>> formatted_string
'My name is John Doe and I am 30 years old.'

```

__Inserting expressions__

```python
>>> age = 30
>>> formatted_string = (
... 'The square of my age is {sqage}.'
... .format(sqage=age**2))
>>> formatted_string
'The square of my age is 900.'


>>> ('{quantity} {item} cost ${price}'.format (
...     quantity=6,
...     item='bananas',
...     price=1.74)
... )
'6 bananas cost $1.74'

```

## Format String

```
{[<name>][!<conversion>][:<format_spec>]}
```

|Component|Meaning|
|---------|-------|
| `name` |Specifies the source of the value to be formatted|
|`conversion`|Indicates which standard Python function to use to perform the conversion|
| `format_spec` |Specifies more detail about how the value should be converted|

For `conversion` the following are useful conversions
* !s str()
* !r repr()
* !a ascii()

```python
>>> '{0!s}'.format(1948)
'1948'
>>> '{0!r}'.format(1948)
'1948'
>>> '{0!a}'.format(1948)
'1948'

```

For `format_spec` the following

`:[[<fill>]<align>][<sign>][#][0][<width>][<group>][.<prec>][<type>]`

|Indicator|Effect|
|------------|------|
| : |	Separates the <format_spec> from the rest of the replacement field|
|`fill`|	Specifies how to pad values that don’t occupy the entire field width|
|`align`|	Specifies how to justify values that don’t occupy the entire field width|
|`sign`|	Controls whether a leading sign is included for numeric values|
| #	|Selects an alternate output form for certain presentation types|
|0|	Causes values to be padded on the left with zeros instead of ASCII space characters|
|`width`|	Specifies the minimum width of the output|
|`group`|	Specifies a grouping character for numeric output|
|`.prec`|	Specifies the number of digits after the decimal point for floating-point presentation types, and the maximum output width for string presentations types|
|`type`|	Specifies the presentation type, which is the type of conversion performed on the corresponding argument|


For the values of `type`:

|Type indicator	|Presentation Type|
|-------|-----------------|
|b|	Binary integer|
|c|	Single character|
|d|	Decimal integer|
|e or E	| Exponential|
|f or F	| Floating point|
|g or G	| Floating point or Exponential|
|o|	Octal integer|
|s|	String|
|x or X|	Hexadecimal integer|
|%|	Percentage|

```Python

>>> import math

>>> '%d' % 1948
'1948'


>>> '{:d}'.format(1948)
'1948'


>>> '%.3f' %  math.pi
'3.142'


>>> '{:.3f}'.format(math.pi)
'3.142'


>>> '%s' % 'foobar'
'foobar'


>>> '{:s}'.format('foobar')
'foobar'


>>> '%x' % 31
'1f'
>>> '{:x}'.format(31)
'1f'

```

## f-string

```python
>>> import math

>>> name, age = "Alice", 30
>>> f"My name is {name} and I am {age} years old."
'My name is Alice and I am 30 years old.'


>>> x, y = 5, 10
>>> f"The sum of {x} and {y} is {x + y}."
'The sum of 5 and 10 is 15.'


>>> pi = 3.14159265
>>> f"The value of pi is approximately {math.pi:.2f}."
'The value of pi is approximately 3.14.'

```
# Delete names from space

There are different ways to delete all declared variables in a j
upyter python notebook, depending on your needs and preferences.
Here are some possible methods:

- You can use the magic command `%reset` to clear all variables from
the interactive namespace¹. This will prompt you to confirm your
action, unless you use the `-f` option to force it. For example:

```
%reset -f
```

- You can also use the `del` keyword to delete specific variables or
objects from memory. For example:

```python
>>> var_a, var_b, var_c =  3, 4, 5
>>> var_a, var_b, var_c
(3, 4, 5)
>>> 'var_a' in locals(), 'var_b' in locals(), 'var_c' in locals()
(True, True, True)
>>> 'var_a' in globals(), 'var_b' in globals(), 'var_c' in globals()
(True, True, True)

>>> del var_a, var_b, var_c
>>> 'var_a' in locals(), 'var_b' in locals(), 'var_c' in locals()
(False, False, False)
>>> 'var_a' in globals(), 'var_b' in globals(), 'var_c' in globals()
(False, False, False)

```

- Another option is to use the `globals()` or `locals()` functions to
get a dictionary of global or local variables, and then iterate
over them to delete them. For example:

```
for var in list(globals().keys()):
    if var[0] != '_': # avoid deleting built-in variables
        del globals()[var]
```

- If you want to delete all variables that are defined after a certain
cell, you can try to store a backup of the variables before that cell
using the `copy` module, and then restore them later. You can also use
the `dir()` function to get a list of the names of the variables in the
current scope, and compare it with the backup list to delete the
new ones². For example:

```
# Store original values
from copy import deepcopy
bckp_a = deepcopy(var_a)
bckp_b = deepcopy(var_b)
dir_bckp = deepcopy(dir()) # store defined variables at this point

# Do your stuff
var_a = some_func(var_a)
var_b = some_other_func(var_a)
var_c = some_value

# Restore original values
var_a = deepcopy(bckp_a)
var_b = deepcopy(bckp_b)

# Delete newly created variables
for var in dir():
    if var == 'dir_bckp': # preserve dir_bckp
        continue
    elif var not in dir_bckp: # delete new variables
        del globals()[var]
```

Source: Conversation with Bing, 17/08/2023
(1) python - Viewing all defined variables -
Stack Overflow. https://stackoverflow.com/questions/633127/viewing-all-defined-variables.

(2) python - jupyter delete all variables after cell - Stack Overflow.
https://stackoverflow.com/questions/45927797/jupyter-delete-all-variables-after-cell.

(3) Data Analysis and Visualization with pandas and Jupyter Notebook in
.... https://www.digitalocean.com/community/tutorials/data-analysis-and-visualization-with-pandas-and-jupyter-notebook-in-python-3.

# Modules

## Module search path

* Current Directory
* `PYTHONPATH` environment variable
* Installation-dependent list

```python
>>> import sys
>>> sys.path   # doctest: +SKIP
```

```python
>>> import doctest
>>> doctest.__file__ # doctest: +SKIP
'/usr/lib/python3.8/sys.py'
```

# Distutils

Python's [Distutils][] is a **mechanism to distribute Python packages
and extensions** that is provided in the Python standard library.
It provides support for building and installing additional modules
into a Python installation, which may be either pure Python,
or extension modules written in C, or collections of Python packages
that include both. It also provides a command-line interface that
allows you to query the metadata fields of a project, create source
and binary distributions, and register your project with the
Python Package Index.

Distutils is a tool for packaging and distributing Python modules that
can be installed by other users.

## Setup.py

In Python, `setup.py` is a file that is used to [setup, build and distribute][]
Python packages. It typically contains information about the package,
such as its name, version, and dependencies, as well as instructions
for building and installing the package. The `setup.py` file is the
centre of all activity in using the Distutils, a set of tools for
packaging and distributing Python modules. The `setup.py` file can be
executed by using various commands, such as:

```bash
python setup.py build # to build the package
python setup.py install # to install the package
python setup.py sdist # to create a source distribution
python setup.py bdist # to create a binary distribution
```

The `setup.py` file is Python's answer to a multi-platform installer
and make file. It allows you to create and distribute Python packages
that can be installed by other users.

[setup, build and distribute]: https://docs.python.org/3/distutils/setupscript.html#writing-the-setup-script

[Distutils]: https://docs.python.org/3/distutils/introduction.html#an-introduction-to-distutils

[doctest ellipsis]: https://docs.python.org/3/library/doctest.html#option-ELLIPSIS
[docktest skip]: https://docs.python.org/3/library/doctest.html#option-SKIP
[Choose a License]: https://choosealicense.com/
[git python ignore]: https://github.com/github/gitignore/blob/main/Python.gitignore