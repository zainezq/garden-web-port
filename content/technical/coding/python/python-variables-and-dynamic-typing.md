---
title: Python Variables & Dynamic Typing
date: 2025-06-06
tags: [ "technical", "programming", "python" ]
---

## Dynamically Typed

Python is a dynamically typed language, which means:

* **You don't declare variable types** explicitly.
* Python **infers the type at runtime** based on the value assigned.
* **You can reassign variables to values of different types**.

Example:

```python
x = 42          # x is an int
x = "hello"     # now x is a str
x = 3.14        # now x is a float
```

## Rules for Variable Names

Valid:

* Must begin with a letter (a–z, A–Z) or underscore (`_`)
* Can contain numbers after the first character
* Are case-sensitive (`var` and `Var` are different)

Invalid:

* Starting with a number (`2x = 10`)
* Containing special characters (`@`, `#`, etc.)
* Matching Python keywords like `for`, `class`, `if`, etc.


## Reassigning and Type Changes

You can reassign a variable to another value (even of a different type):

```python
x = 100     # int
x = "abc"   # now a string
x = [1, 2]  # now a list
```

**Python doesn't "change the type" of the variable, it just rebinds the name to a new object.**


## Multiple Assignments

Python supports assigning values to multiple variables in one line:

### Same value to multiple variables:

```python
a = b = c = 0
```

### Different values to different variables:

```python
x, y, z = 1, 2, 3
```

**Python uses tuple unpacking here**.

## Variable References & Object Identity

In Python:

* Variables are **references** to objects.
* Use `id()` to check the identity (memory address) of an object.

```python
a = 10
b = a
print(id(a) == id(b))  # True
```

But if you assign a new value:

```python
b = 20
print(id(a) == id(b))  # False
```

## Type Checking

You can check a variable's type using:

### `type()` function:

```python
x = 3.14
print(type(x))  # <class 'float'>
```

### `isinstance()` function:

```python
print(isinstance(x, float))  # True
print(isinstance(x, int))    # False
```

## Dynamic Typing vs Static Typing

| Feature        | Dynamic Typing (Python) | Static Typing (C, Java) |
|----------------|-------------------------|-------------------------|
| Type declared? | No                      | Yes                     |
| Checked when?  | Runtime                 | Compile-time            |
| Flexibility    | High                    | Low                     |
| Risk           | Runtime errors          | Compile-time errors     |

---

## Mutability and Variables

Objects can be:

* **Mutable**: Can be changed after creation (e.g., lists, dicts)
* **Immutable**: Cannot be changed (e.g., int, str, tuple)

This affects variable behavior:

```python
a = [1, 2, 3]
b = a
b.append(4)
print(a)  # [1, 2, 3, 4] — both a and b refer to the same list
```

But with immutable types:

```python
x = 5
y = x
y += 1
print(x)  # 5 — x remains unchanged
```

## Garbage Collection

When a variable is no longer used (no references to an object), Python automatically frees up memory using garbage
collection.

```python
x = "hello"
x = None  # previous string object "hello" may be garbage-collected
```