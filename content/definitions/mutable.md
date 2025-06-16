---
title: Mutability
date: 2025-06-15
tags: [ "definition" ]
---

A mutable object can be changed after it's created, and an immutable object can't. 

```python
x = [1, 2, 3] # This is an array
x[0] = 4  # x is mutable
y = (1, 2, 3) # This is a tuple
y[0] = 4  # y is immutable
```