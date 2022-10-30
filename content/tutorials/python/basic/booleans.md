---
title: Booleans
---

## Introduction

A Boolean (named after [George Boole](https://en.wikipedia.org/wiki/George_Boole)) value is a value that is either true or false. In Python, Booleans are implemented as `bool`. Booleans are used to represent not only truth values (true/false) but any two-state data such as good/bad, passed/failed, success/failure, male/female, and so on.

## Domain

The domain of the `bool` type consists of only two values: `True` and `False` (remember that Python is case-sensitive).

```python
type(True)
```

```output
bool
```

```python
type(False)
```

```output
bool
```

## How to get a bool?

### From a bool literal

We can get a `bool` from a direct assignment with the literals `True` and `False`.

```python
is_male = True
```

```python
is_male
```

```output
True
```

```python
type(is_male)
```

```output
bool
```

### From an expresion

We can also get a `bool` from an expression that produces a bool. Normally, it is a comparison. Here is the list of comparison operators in Python, and they are very intuitive.

```python
is 	# the same identity
== 	# is equal
!= 	# is not equal
>	# greater than
>=	# greater than or equal
<	# less than
<= 	# less than or equal
```

Let's try some examples.

```python
# Create four variables
x = 1000
y = 2000
z = 1000
t = x
```

The `is` operator.

```python
# Are x and y aliases?
x is y
```

```output
False
```

```python
# Are x and t aliases?
x is t
```

```output
True
```

The `==` operator.

```python
# Are x and y equal?
x == y
```

```output
False
```

```python
# Are x and z equal?
x == z
```

```output
True
```

```python
# Are x and t equal?
x == t
```

```output
True
```

For the other operators, please try them yourself.

### From a functional call

Some functions are designed to answer Yes/No questions, and it makes sense for them to return a `bool`. For example, the `isinstance()` function check if an object belongs to a specific type. If the answer is yes, then it returns `True`. Otherwise, it returns `False`.

```python
# Create two variables
x = 5
y = 2.5
```

```python
# Is x an integer?
isinstance(x, int)
```

```output
True
```

```python
# Is y an integer?
isinstance(y, int)
```

```output
False
```

## Common operations

Usually, we only perform logical operations on Booleans. There are three logical operators namely `and`, `or`, and `not`.

The logical `and` is a binary operator; it needs two arguments, each on one of its sides. `x and y` will return `True` only if both `x` and `y` are `True`. Otherwise, it will return `False`.

```python
print(True and True)
print(True and False)
print(False and True)
print(False and False)
```

```output
True
False
False
False
```

The logical `or` is also a binary operator. `x or y` will return `False` only if both `x` and `y` are `False`. Otherwise, it will return `True`.

```python
print(True or True)
print(True or False)
print(False or True)
print(False or False)
```

```output
True
True
True
False
```

The logical not is a unitary operator; it takes only one argument and returns the negation of the argument. `not x` will return `True` if `x` is `False` and return `False` if `x` is `True`.

```python
print(not True)
print(not False)
```

```output
False
True
```

## When uses bool?

Booleans are normally used as conditions for branching statements such as `if` or `match`. We will learn branching in detail in lessons about control flows. For now, just consider a very simple example.

```python
grade = 8

if grade >= 4:
    print("Passed")
else:
    print("Failed")
```

```output
Passed
```

In the above example, we see a simple `if else` structure that works as follows: if the condition in the `if` part is true, then the indented code block under `if` will be executed. Otherwise (the condition is false), the indented code block under `else` will be executed.

Here we have a comparison `grade >= 4` in the `if` part. Since `grade = 8`, this comparison returns `True`. Thus, the condition is true, and we see `Passed` printed out. If we change `grade` to a value less than `4`, we will see `Failed` printed out. Let's try it.

```python
grade = 2

if grade >= 4:
    print("Passed")
else:
    print("Failed")
```

```output
Failed
```

## Conversion to bool

Sometimes, we might have to convert an object from one type to another. This action is known by many names, including type conversion, type casting, and type coercion.

To convert an object to a bool, we use the `bool()` function. Here is a rule of thumb.

- Zero, `None`, and values that are considered "empty" will be converted to `False`.
- Non-zero and non-empty values will be converted to `True`.

Let's see some examples.

From `None`

```python
bool(None)
```

```output
False
```

From ints

```python
bool(0)
```

```output
False
```

```python
bool(-1)
```

```output
True
```

From floats

```python
bool(0.0)
```

```output
False
```

```python
bool(1.5)
```

```output
True
```

From strings

```python
bool("")
```

```output
False
```

```python
bool("Hello")
```

```output
True
```

From lists

```python
bool([])
```

```output
False
```

```python
bool([1, 2, 3])
```

```output
True
```

## Implicit type casting

Python sometimes performs type conversion implicitly. Recall that `if` always expects a `bool`. If it is not the case, Python will perform an implicit conversion to get a `bool` as in the following example.

```python
students = []

if students:
    print("There is at least 1 student")
else:
    print("There is no student")
```

```output
There is no student
```

Here `students` is an empty `list`, not a `bool`. So to make `if students` work, Python has to convert `students` to a `bool`, and from the previous section, you know that an empty list, when converted to `bool`, will produce `False`. That's why we see `There is no student` printed out.
