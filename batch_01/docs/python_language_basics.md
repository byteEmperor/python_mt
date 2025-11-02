# Python Language Basics
This file provides an overview of essential Python programming concepts and language mechanics. 

## Indentation, not braces
Python uses whitespaces (tabs or spaces) to structure code instead of using braces.

A colon (:) denotes the start of an indented code block after which all of the code must be indented by the same amount
until the end of the block.

Semicolons can be used to separate multiple statements on a single line, which is discouraged in Python.

## Everything is an object
An important characteristic of the Python language is the consistency of its object model. Every number, string, data 
structure, function, class, module, and so on exists in the Python interpreter in its own "box", which is referred to
as a Python object. Each object has an associated type (e.g., string or function) and internal data. In practice this 
makes the language very flexible, as even functions can be treated like any other object.

## Duck typing
Often you may not care about the type of an object but rather only whether it has certain methods or behaviour. This is
sometimes called "duck typing". For example, you can verify that an object is iterable if it implemented the iterator 
protocol. For many objects, this means it has a <__iter__> "magic method", though an alternative and better way to 
check is to try using the <iter> function:
$ def isiterable(obj):
$   try:
$       iter(obj)
$       return True
$   except TypeError:
$       return False

A place where this functionality is very useful is when writing functions that can accept multiple kinds of input. A 
common case is writing a function that can accept any kind of sequence (list, tuple, ndarray) or even an iterator. You
can check first if the object is a list (or a NumPy array) and, if it is not, convert it to be one:
$ if not isinstance(x, list) and isiterable(x):
$   x = list(x)

## Binary operators and comparisons
To check if two references refer to the same object, use the <is> keyword. <is not > is also perfectly valid.
$ a is b
$> True

A very common use of <is> and <is not> is to check if a variable is <None>, since there is only one instance of <None>.

A good overview of the binary operators can be found on page 37.

## Strings
You can write string literals using either single quotes <'> or double quotes <">. For multiple strings with line 
breaks, you can use triple quotes, either <'''> or <""">.

Python strings are immutable; you cannot modify a string.

Many Python objects can be converted to a string using the <str> function:
$ a = 5.6
$ s = str(a)

The backlash character <\> is an escape character, meaning it is used to specify special characters like newline <\n> or
Unicode characters. To write a string literal with backslashes, you need to escape them:
$ s = '12\\34'
$> 12\34

Instead of escaping, you can preface the leading quote of the string with <r>, which means that the characters should be 
interpreted as is. The <r> stands for raw:
$ s = r'this\has\no\special\characters'

## String Templating
String objects have a <format> method that can be used to substitute formatted arguments into the string. A good example
is the following:
$ template = '{0:.2f} {1:s} are worth US${2:d}'
> {0:.2f} means to format the first argument as a floating-point number with two
decimal places.
> {1:s} means to format the second argument as a string.
> {2:d} means to format the third argument as an exact integer.

## Type Casting
The <str>, <bool>, <int>, and <float> types are also functions that can be used to cast values to those types:
$ fval = float(s)

## Ternary expressions
A ternary expression in Python allows one to combine an <if-else> block that produces a value into a single line or
expression. The syntax for this in Python is:
$ value = true-expr if condition else false-expr




