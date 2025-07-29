---
layout: post
title: "Python Tutorial" 
date: 2025-07-20
categories: [blog/python/]
---

# Python Tutorial: From Beginner to Intermediate

This tutorial covers the fundamentals of Python, including syntax basics, data structures, control flow, and advanced topics for experienced programmers.

## 1. Getting Started
### What is Python?
Python is a high-level programming language known for its simplicity and readability.
- **Why learn Python?**  
  - Easy to read and write code (less boilerplate).  
  - Extensive standard library for built-in functions.  
  - Supports multiple programming paradigms (procedural, object-oriented, functional).  

### Installing Python
1. Download from [Python Official Website](https://www.python.org/).
2. On Windows: Run the installer and choose **MSI** installation.
3. For Linux/MacOSX: Use your package manager to install Python.

---

## 2. Basic Syntax

### Variables
In Python, variables are declared without explicit declaration (no need for `var()` or `int()`).

```python
# Example:
x = "Hello"
y = 5
z = True  # Boolean type
```

### Comments
- Single-line comment: `# This is a comment`
- Multi-line comment using triple quotes:

```python
"""
This is a multi-line comment.
It can span multiple lines and still be readable.
"""

```

---

## 3. Data Structures

### Numbers (ints, floats)
Python supports integers (`int`) and floating-point numbers (`float`).

```python
a = 10   # int  
b = 5.67  # float  
c = True  # Boolean type is a subclass of int in Python
```

### Strings
Strings are sequences of characters enclosed in quotes.

```python
s = "Hello, World!"  # Double-quoted strings recommended for readability.
print(s)            # Outputs: Hello, World!
```

### Lists and Tuples

#### Lists
A list is an ordered collection of elements:

```python
my_list = [10, 20.5, True]  
print(my_list[0])          # Outputs: 10  
print(len(my_list))        # Outputs: 3 (since it's mutable)
```

#### Tuples
A tuple is similar to a list but immutable:

```python
my_tuple = ("Hello", "World") 
# Cannot change the elements of a tuple after creation.
```

### Sets and Dictionaries

#### Sets
An unordered collection of unique elements.

```python
s = {1, 2, 3}  
if 2 in s:
    print("Element found!")  
else:  
    print("Element not present.")
```

#### Dictionaries
A dictionary stores key-value pairs:

```python
d = {"key": "value", ("another key"): None}
print(d["key"])   # Outputs: value
# Note: Keys must be immutable types (e.g., strings, numbers).
```

---

## 4. Control Flow

### Conditional Statements
Use `if`, `elif`, and `else` statements.

```python
x = 10  
y = 5  

if x > y:
    print("x is greater than y.")
elif x == y: 
    print("x equals y.")
else:
    print(f"Wait, {x} can't be less than a positive number like {y}.")
```

### Loops
Python supports `for` and `while` loops.

#### For Loop

```python
# Iterate over elements in an iterable (e.g., list):
my_list = [10, 20.5, True]  
for item in my_list:
    print(item)
print("Loop completed.")
```

#### While Loop

```python
count = 0  

while count < 3: 
    print(f"Count is {count}")
    count += 1
# Outputs:
# Count is 0
# Count is 1
# Count is 2  
```

---

## 5. Functions and OOP (Object-Oriented Programming)

### Defining a Function

```python
def greet(name):
    """Returns a greeting message."""
    return f"Hello, {name}!"

print(greet("Alice"))   # Outputs: Hello, Alice!
```

### Classes in Python

#### Example of a Simple Class:

```python
class Rectangle:
    def __init__(self, length, width):  
        self.length = length  # Instance variable
        self.width = width
    
    def area(self):
        """Returns the area of the rectangle."""
        return self.length * self.width  

# Creating an instance:
r1 = Rectangle(2.0, 3.5)  
print(r1.area())   # Outputs: 7.0
```

---

## 6. Advanced Topics

### Error Handling (Exception Handling)

```python
try:
    x = int(input("Enter a number: ")) 
except ValueError:
    print("Please enter a valid integer.")
else:
    y = float(x)
    z = y / 2  
    print(f"The half of {x} is {z}.")
```

### Lambda Functions

```python
# Example lambda function that adds two numbers:
add = lambda x, y: x + y  

print(add(3,5))   # Outputs: 8
```

---

## 7. File Handling

Reading and writing files in Python:

```python
# Reading a file line by line:
file_name = "data.txt"  
with open(file_name, 'r') as f:
    for line in f:
        print(line.strip())
        
# Writing to a new file (note: mode is read-write):
with open("new_file.txt", 'w') as f:
    f.write("Hello from Python!")
```

---

## 8. Modules and Packages

### Importing Modules

```python
import math  
print(math.sqrt(25))   # Outputs: 5.0  

# Using a module's function without importing the entire module (optional):
sqrt_16 = lambda x=4: math.sqrt(x)
print(sqrt_16())    # Outputs: 2.0

from math import sqrt as m_sqrt  
print(m_sqrt(9))     # Outputs: 3.0
```

### Installing Packages via pip

```bash
pip install numpy  
import numpy as np  
arr = np.array([1,2,3]) 
print(arr)   # Outputs: [1 2 3]
```

---