# Python notes

# Doctest

To test the code in this README run the following python script

```bash
python -m doctest README.md  -v
```

Ellipsis in doctests

Whenever possible, I extracted the Python console listings in this book
from doctest to ensure accuracy. When the output was too long, the
elided part is marked by an ellipsis (...)

doctest: +ELLIPSIS directive to make the doctest pass:



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