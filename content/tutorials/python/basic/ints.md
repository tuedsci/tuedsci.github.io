---
title: Ints
---

## Introduction

Integers are whole numbers without decimal parts. They can be negative (e.g., `-5`, `-1000`), positive (e.g., `1`, `2000`), or zero (i.e., `0`). Integers in Python are implemented as `int` and are usually called ints.

```python
x = 10
```

```python
x
```

```output
10
```

```python
type(x)
```

```output
int
```

## Domain

As in mentioned in the previous lesson, an int can be arbitrarily long; as long as it can fit into memory without being overflowed. Thus, technically, the domain of is `int` type is the set of all integers.

```python
# A very long integer
x = -3565622255488771132323355767676856586585965999884384
```

```python
x
```

```output
-3565622255488771132323355767676856586585965999884384
```

```python
type(x)
```

```output
int
```

## How to get an int?

### From an int literal

We can get an `int` from a direct assignment with an `int` literals.

```python
x = 100
```

```python
x
```

```output
100
```

```python
type(x)
```

```output
int
```

### From an expression

We can also get an `int` from an expression that produces an `int`. Normally, they are math expressions involving integers. Here are some examples.

```python
# Create two integers
x = 100
y = 2
```

Addition

```python
# Value
x + y
```

```output
102
```

```python
# Type
type(x + y)
```

```output
int
```

Subtraction

```python
# Value
x - y
```

```output
98
```

```python
# Type
type(x - y)
```

```output
int
```

Multiplication

```python
# Value
x * y
```

```output
200
```

```python
# Type
type(x * y)
```

```output
int
```

Exponentiation

```python
# Value
x ** y
```

```output
10000
```

```python
# Type
type(x ** y)
```

```output
int
```

The standard division with the `/` operator, however, always produces a `float` even if the result is an integer mathematically.

```python
# Value
x / y
```

```output
50.0
```

```python
# Type
type(x / y)
```

```output
float
```

### From a function call

Many functions return an int as a result. For example, the `len()` function counts the number of elements in a collection and returns the count as an int.

```python
len([1, 2, 5, 8, 9])
```

```output
5
```

## Common operations

Since ints are numbers, we can perform math and comparison operations on them.

### Math operations

As discussed in the previous section, operations such as `+`, `-`, `*`, and `**` on ints produce an int, while the standard division (or real division) using `/` produces a `float`.

Besides these operations, we can perform integer division (using `//`) and modulo division (using `%`) on integers, and the result will be an int. For example, when dividing `7` by `3`, we get `2` as the quotient and `1` as the remainder because `7 = 3 * 2 + 1`.

```python
# Get the quotient
7 // 2
```

```output
3
```

```python
# Get the remainder
7 % 2
```

```output
1
```

### Comparison operations

We can compare two integers, and the result will be a Boolean as in the examples below.

```python
1000 == 2000
```

```output
False
```

```python
1000 != 2000
```

```output
True
```

```python
1000 < 2000
```

```output
True
```

```python
1000 >= 2000
```

```output
False
```

## When uses int?

We use ints whenever it makes sense to represent some value as an integer. Often, it is a count of something, for example, the number of households in a district, the number of students in a class, and so on.

```python
# Initiate the number of households
num_households = 1250
```

```python
# Now 10 more households move into the district
num_households = num_households + 10
```

```python
# The updated number of households
num_households
```

```output
1260
```

## Conversion to int

Similar to `bool`, we can convert a value to `int` using the `int()` function. However, not every value can be converted to `int`; only those considered "compatible". Let's see some examples.

### From Booleans

When converting a bool to int, `True` will produce `1` and `False` will produce `0`.

```python
int(True)
```

```output
1
```

```python
int(False)
```

```output
0
```

### From floats

When converting a float to int, the decimal part is truncated.

```python
int(10.7)
```

```output
10
```

```python
int(-10.3)
```

```output
-10
```

### From strings

When converting a string to int, the string must "look like" an integer.

```python
# No problem
int("10")
```

```output
10
```

```python
# Negative sign is interpreted correctly
int("-10")
```

```output
-10
```

```python
# Leading and trailing spaces are ignored
int("   15   ")
```

```output
15
```

```python
# Error because of the dot (.) character
int("10.5")
```

```output
ValueError: invalid literal for int() with base 10: '10.5'
```

```python
# Error because of the comma (,) character
int("1,000")
```

```output
ValueError: invalid literal for int() with base 10: '1,000'
```

## Some fun examples

### Odd or even?
Let's say we are given an integer `x` and have to decide whether it is an odd or an even number. How can we solve this?

Recall that an even number is divisible by `2`, but an odd number is not. What does it mean "`x` is divisible by `2`" in Python? It means the remainder `x % 2` is zero. So we have a solution as follows.

```python
x = 6

if x % 2 == 0:
    print("Even")
else:
    print("Odd")
```
```output
Even
```

Here we see `Even` printed out because `x = 6` is indeed an even number. In the `if` part, `6 % 2` produces `0`, so the comparison (equivalent to `0 == 0`) is evaluated as `True`. If you change `x` to `-7` for example, you will see `Odd` printed out.


```python
x = -7

if x % 2 == 0:
    print("Even")
else:
    print("Odd")
```
```output
Odd
```
### Odd or even with implicit type casting

Recall from the last lesson that `if` always expects a bool. If the condition is not of type `bool`, Python will try to (implicitly) convert it to `bool`. So the previous example can be succinctly re-written as follows.

```python
x = 6

if x % 2:
    print("Odd")
else:
    print("Even")
```

```output
Even
```

Here `6 % 2` gives a `0` so `if x % 2:` is equivalent to `if 0:`. Since `0` is not a bool, Python has to do an implicit conversion, and `bool(0)` gives `False`. Thus, we have to adjust the logic and print out `"Odd"` for this case because the condition is always evaluated as `False` for even numbers, and the indented code block under the `else` part is executed, not the one under the `if` part.

Although this solution is cool, I wouldn't recommend it. It makes the code harder to read. Recall Zen of Python.

> Explicit is better than implicit
