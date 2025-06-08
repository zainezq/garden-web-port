---
title: Python Syntax & Indentation
date: 2025-06-08
tags: [ "technical", "programming", "python" ]
---

# Syntax

The [[syntax.md | syntax]] of Python is similar to those of other programming languages, below is a summary and a quick
reference.

## Comments

A single-line comment starts with the `#` character and extends to the end of the line.

```python
# This is a single-line comment
```

A multi-line comment starts with `"""` and ends with `"""`. It can span multiple lines.

```python
"""
This is a multi-line comment
"""
```

## Indentation

Python uses indentation to indicate block structure. Indentation is used to indicate that a block of code is part of a
larger block of code.

```python
if condition:
    # This is a block of code that is part of the if statement
    print("Hello world!")
```

In other languages, indentation is used to make the code look more readable. In Python, indentation is used to
indicate the block structure of the code, hence why it is important.

## Arithmetic

The following below are the primary [[arithmetic.md | arithmetic]] operators, which can be applied to literal numbers,
variables, or
some combinations:

- `+` for addition
- `-` for subtraction
- `*` for multiplication
- `/` for division
- `%` for modulus (returns the remainder)
- `**` for exponentiation

Examples:

```python
2 + 3
# 5
2 - 3
# -1
2 * 3
# 6
2 / 3
# 0.6666666666666666
2 % 3
# 2
2 ** 3
# 8
```

## Plus-Equals Operator

The `+=` operator is used to add and assign a value to a variable:

```python
x += 1
```

If used on a string, it concatenates the string to the variable:

```python
x = "hello"
# x is now "hello"

x += " world"
# x is now "hello world"
```

## Variables

A variable is a named location in memory that can hold a value. It can be assigned a value using the `=` operator:

```python
x = 5
# the variable x now holds the value 5
```

## Data Types

Python has the following data types:

- `int` for integers
- `float` for floating-point numbers
- `str` for strings
- `bool` for booleans
- `list` for lists
- `tuple` for tuples
- `dict` for dictionaries
- `set` for sets

```python
x = 5
# x is now an integer

x = 5.0
# x is now a float

x = "hello"
# x is now a string

x = True
# x is now a boolean

x = [1, 2, 3]
# x is now a list

x = (1, 2, 3)
# x is now a tuple

x = {"a": 1, "b": 2}
# x is now a dictionary

x = {1, 2, 3}
# x is now a set
```

## Control Structures

Python has the following control structures:

- `if` for conditional statements
- `for` for loops
- `while` for loops
- `range()` for loops

```python
if x > 0:
    print("x is positive")
elif x < 0:
    print("x is negative")
else:
    print("x is zero")
```

```python
for i in range(5):
    print(i)
```

```python
while x > 0:
    print(x)
    x -= 1
```

```python
for i in range(5):
    print(i)
```

## Reserved Words

Python has the following reserved words:

| Reserved Word | Description         | Example                                       |
|---------------|---------------------|-----------------------------------------------|
| `and`         | Logical and         | `x > 0 and x < 10`                            |
| `as`          | Assign              | `import math as m`                            |
| `assert`      | Assert              | `assert x > 0, "x is negative"`               |
| `break`       | Break               | `for x in range(10): if x == 5: break`        |
| `class`       | Class definition    | `class Person: pass`                          |
| `continue`    | Continue            | `for x in range(10): if x % 2 == 0: continue` |
| `def`         | Function definition | `def add(x, y): return x + y`                 |
| `del`         | Delete              | `del x`                                       |
| `elif`        | Else if             | `if x > 0: ... elif x < 0: ...`               |
| `else`        | Else                | `if x > 0: ... else: ...`                     |
| `except`      | Exception handling  | `try: ... except: ...`                        |
| `finally`     | Finally             | `try: ... finally: ...`                       |
| `for`         | For loop            | `for x in range(10): ...`                     |
| `from`        | Import from         | `from math import *`                          |
| `global`      | Global variable     | `x = 5; global x`                             |
| `if`          | If                  | `if x > 0: ...`                               |
| `import`      | Import              | `import math`                                 |
| `in`          | In                  | `x in [1, 2, 3]`                              |
| `is`          | Is                  | `x is y`                                      |
| `lambda`      | Lambda function     | `f = lambda x, y: x + y`                      |
| `nonlocal`    | Nonlocal variable   |                                               |
| `not`         | Not                 | `not x`                                       |
| `or`          | Logical or          | `x > 0 or x < 10`                             |
| `pass`        | Pass                | `if x > 0: pass`                              |
| `raise`       | Raise exception     | `raise ValueError("x is negative")`           |
| `return`      | Return              | `def add(x, y): return x + y`                 |
| `try`         | Try                 | `try: ... except: ...`                        |
| `while`       | While loop          | `while x > 0: ...`                            |
| `with`        | With                | `with open("file.txt") as f: ...`             |
| `yield`       | Yield               |                                               |

## Functions

Functions are defined using the `def` keyword:

```python
def add(x, y):
    return x + y
```

## Classes

Classes are defined using the `class` keyword:

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
```

## Modules

Modules are defined using the `import` keyword:

```python
import math
```

## File I/O

File I/O is defined using the `open` function:

```python
f = open("file.txt", "r")
``` 

## Multiline Strings

Multiline strings are defined using triple quotes:

```python
s = """This is a multiline string"""
```

## Docstrings

Docstrings are defined using triple quotes:

```python
def add(x, y):
    """
    This is a docstring
    """
    return x + y
```

## User Input

User input is defined using the `input` function:

```python
name = input("\nWhat is your name? ")
```

* Note that the `\n` is used to create a new line.

## Command Line Arguments

Command line arguments are defined using the `sys.argv` module:

```python
import sys
print ('argument list', sys.argv)
name = sys.argv[1]
print ("Hello {}. How are you?".format(name))
```

This example is taken from [this](https://www.tutorialspoint.com/python/python_command_line_arguments.htm) link.

The output of the above code will be:

```python
C:\Python311>python hello.py user
argument list ['hello.py', 'user']
Hello user. How are you?
```
