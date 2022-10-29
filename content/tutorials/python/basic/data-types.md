---
title: Python data types
---

A large part of programming is dealing with data. However, machines don't understand real-life data, so our job is to represent them in ways that machines can understand through a set of pre-defined data types. In this lesson, you will learn what they are, their classification, a birds-eye view of the common data types, and an important concept called dynamic typing.

## What are data types?

Formally speaking, a data type (or just type) is a set of possible values that a variable of this type can assume (called the domain) together with a set of allowed operations we can perform on it.

Consider the following example. Suppose we want a variable for the number of households in a district. The real-life value for this measurement should be a natural number (or a non-negative integer). Thus, Python provides the `int` type to represent, store, and manipulate values of this kind. Formally speaking, the `int` type defines two things.

- A set of possible values: all integers such as `0`, `1`, `-2`, or `1000000`
- A set of allowed operations: we can perform math operations such as `+`, `-`, `*`, and `/` on integers. However, we cannot convert an integer to uppercase or lowercase. Such operations are not allowed for integers but are for the string type.

## Programming and reality

It should be noted that data types are just approximations of reality defined by a programming language, and they might not fully mirror their real-life counterparts. Take Python's `float` type for example. The `float` type is designed to represent real-numbered values such as salary, revenue, and profit. However, mathematically, there are infinitely many real numbers, which form the whole continuum. Thus, there is no way that machines (with limited memory) can represent all real numbers (with infinite precision. As a result, the domain of the `float` type is just a set of real numbers up to some given precision, not all real numbers. However, this approximation is sufficient in most practical applications.

## Built-in and user-defined types

We can categorize data into two major groups: built-in and user-defined.

- **Built-in types** are part of the language and are readily available when we installed Python. 
- **User-defined types** are constructed by programmers based on the built-in types when the built-in types are not sufficient for more complex applications.

User-defined types can be (informally) further divided into two groups: off-the-shelf (OTS) user-defined types and handcrafted (HC) user-defined types (I am sorry for not being able to think of any better names).

- **OTS types** are developed by professional programmers, and they are often shipped as part of third-party packages. For example, the NumPy package offers a data structure called `numpy.ndarray` for storing and handling data in multi-dimensional arrays.
- **HC types** are developed by YOU when you cannot find any data types (either built-in or OTS) that suit your needs.

This series focuses mostly on common built-in types and perhaps some OTS types, but not HC types. In fact, you rarely have to create HC types when working as a data analyst/scientist even at intermediate levels.

## A birds-eye view

In this section, I will give you a birds-eye view of the type hierarchy in Python. Note that the hierarchy is not exhaustive. I only show common types that, based on my experience, are relevant and important. The main purpose is to provide the fundamentals, not to overwhelm you with types that you will never use.

### Null

Python provides the `NoneType` type whose domain contains only a single value `None`. This type is used to represent the state of being unknown or undefined (a.k.a null) in reality. Often, it is used to denote missing values.

### Truth values

Python offers the `bool` types whose domain has only two possible values: `True` and `False`. This type is used to represent two-state data such as true/false, good/bad, passed/failed, success/failure, male/female, and so on.

### Numbers

Python provides several types for representing numeric data including `int`, `float`, and `complex`. The `int` type is designed for representing integers, and its domain is the set of all integers. The `float` type is designed for representing real numbers; however, as discussed in the previous section, its domain is just a collection of real numbers with a given precision. I will not cover the `complex` type in this series.

### Collections

The data types introduced so far are informally called **scalar types** because an object of these types can only hold a single (or scalar) value. For example, we cannot store two integers in an object of type `int`. If we want to store the scores of 100 students, we have to create 100 objects and associate them with 100 variables. That's an ugly solution.

Fortunately, Python offers some more flexible data structures that can handle a collection of elements under the same variable name such as `list`, `tuple`, `dict`, or `set`. These are called **collection types** (to distinguish them from scalar types).

Collection types can be further divided into three sub-groups as follows.

- Sequence: `list`, `tuple`, `range`, `str`
- Mapping: `dict`
- Set: `set`, `frozenset`

We will learn all of them in detail in future lessons.

### Callables

The data types introduced earlier have the same nature: they are designed to store data. However, you will learn about functions and methods, which are designed to manipulate data, not to store them.

A function is a completely valid object in Python (as valid as an integer), and thus it has a type. The data type of a function is called **callable**. The reason for that name is that the action of using a function is "calling" it. In Python, the technical term for callable is `builtin_function_or_method`.

## Inspecting data types

We can get the type of an object by using the `type()` function. Let's take a look at some examples.

```python
# Type of the None literal
type(None)
```

```output
NoneType
```

```python
# Type of a bool literal
type(True)
```

```output
bool
```

```python
# Type of an int literal
type(5)
```

```output
int
```

```python
# Type of a float literal
type(2.5)
```

```output
float
```

```python
# Type of a string literal
type("Ciao")
```

```output
str
```

## Dynamic typing

Python is dynamically typed, meaning that the type of an object is determined at runtime when the object is created. This is done automatically by Python when it evaluates the value to form the object. Thus, we don't need any kind of "type declaration" like in C/C++ for example.

Be aware that data types in Python are associated with objects, not with variables. Recall that a variable is just a label pasted on a box (an object). We can peel it and paste it on whatever box of whatever type we want. It is the box that has a type, not the label. Let's consider some examples.

```python
x = 5 ** 2
```

In the above assignment, Python evaluates the RHS and comes up with an integer `25`. Then an object of type `int` is created to hold that value. Finally, Python establishes a binding between the variable `x` and the object. Now, let's run the following statement.

```python
type(x)
```

```output
int
```

As you might guess, we get `int` printed out, and some might say "type of `x` is `int`". Technically, it is wrong. The correct statement should be "type of the object that `x` refers to is `int`". Understanding this is important because you won't get confused when seeing something like this.

```python
x = "Ciao"
type(x)
```

```output
str
```

Here you see `str` printed out, not because `x` has changed its type; `x` does not have a type. What has changed is the binding between `x` and the object it refers to. Before, `x` is associated with an object of type `int`, so `type(x)` will print out `int`. But now, `x` is associated with a new object of type `str`, so `type(x)` gives us `str`.
