---
title: Python Data Types
date: 2025-06-16
tags: [ "technical", "programming", "python" ]
---

# Python Data Types

Definition(s):

-  **[[mutable | Mutability]]**

## Basic Data Types

| Type       | Description                 | Example           |
|------------|-----------------------------|-------------------|
| `int`      | Integer numbers             | `x = 5`           |
| `float`    | Floating-point numbers      | `y = 3.14`        |
| `complex`  | Complex numbers             | `z = 2 + 3j`      |
| `str`      | Text/string                 | `name = "Python"` |
| `bool`     | Boolean (True/False)        | `is_valid = True` |
| `NoneType` | Represents absence of value | `x = None`        |

## Collection Types

| Type        | Mutable | Description                    | Example                       |
|-------------|---------|--------------------------------|-------------------------------|
| `list`      | Yes     | Ordered, changeable sequence   | `[1, 2, 3]`                   |
| `tuple`     | No      | Ordered, unchangeable sequence | `(1, 2, 3)`                   |
| `range`     | No      | Immutable sequence of numbers  | `range(5)`                    |
| `dict`      | Yes     | Key-value pairs                | `{"name": "John", "age": 30}` |
| `set`       | Yes     | Unordered, unique elements     | `{1, 2, 3}`                   |
| `frozenset` | No      | Immutable set                  | `frozenset({1, 2, 3})`        |

## Binary Types

| Type         | Mutable | Description                 | Example                |
|--------------|---------|-----------------------------|------------------------|
| `bytes`      | No      | Immutable sequence of bytes | `b'hello'`             |
| `bytearray`  | Yes     | Mutable sequence of bytes   | `bytearray(5)`         |
| `memoryview` | N/A     | Memory view of an object    | `memoryview(bytes(5))` |

# Getting the Data Type

You can use the `type()` function to get the type of a variable:

```python
x = 3.14
print(type(x))  # <class 'float'>
```

# Setting a specific Data Type

You can use the following constructor functions to set a specific data type:

```python
x = int(3.14)  # 3
y = float(5)   # 5.0
z = complex(2, 3)  # (2+3j)
```