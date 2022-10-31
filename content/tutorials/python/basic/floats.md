---
title: Floats
math: true
---

## Introduction

Floats (or floating-point numbers) are real numbers with decimal parts such as `3.14`, `-2.7`, or `0.05`. They are used to represent real-valued data such as distance, salary, sales, profit, price, and so on. Floats in Python are implemented as `float`.

```python
x = 3.14
```

```python
x
```

```output
3.14
```

```python
type(x)
```

```output
float
```

## Domain

Recall from the previous lesson that the float type is just an approximation of the real numbers within a limited range and with fixed precision. In Python, the `float` type is implemented using a 64-bit with double precision, meaning that it can represent values up to approximately $1.798\times 10^{308}$ with 16 significant digits. Beyond this limit, everything is considered infinity (or `inf`). However, this is fine for most practical applications.

## The name float

The name `float` came from the fact that real numbers are represented in the floating-point format in computers. For example, $3.14$ can be represented as $3.14$, $0.314 \times 10^1$, or $31.4 \times 10^{-1}$. You see the decimal point can move around, thus the name floating-point, or float for short. However, you can safely ignore this technical detail and think of a float just as a representation of a real number.

## How to get a float?

### From a float literal

We can get a `float` from a direct assignment with a `float` literal.

```python
x = 3.14
```

```python
x
```

```output
3.14
```

```python
type(x)
```

```output
float
```

Note that `2` is an int literal, but `2.0` or `2.` is a float literal. They are the same in terms of value, just have different types.

### From an expression

We can also get a `float` from an expression that produces a `float`. Normally, they are math expressions involving floats. Here are some examples.

```python
# Create two floats
x = 4.5
y = 1.5
```

Addition

```python
# Value
x + y
```

```output
6.0
```

```python
# Type
type(x + y)
```

```output
float
```

Subtraction

```python
# Value
x - y
```

```output
3.0
```

```python
# Type
type(x - y)
```

```output
float
```

Multiplication

```python
# Value
x * y
```

```output
6.75
```

```python
# Type
type(x * y)
```

```output
float
```

Exponentiation

```python
# Value
x ** y
```

```output
9.545941546018392
```

```python
# Type
type(x ** y)
```

```output
float
```

As discussed in the previous lesson, the real division operator (`/`) always produces a `float` regardless of its operands.

```python
# Divide a float by a float
4.5 / 1.5
```

```output
3.0
```

```python
# Divide an integer by an integer
5 / 3
```

```output
1.6666666666666667
```

### From a function call

Many functions return a float as a result of some numeric computation. For example, the `sum()` takes a list of numbers and computes their sum. If one of the numbers in the list is a float, then the sum will be a float.

```python
sum([1, 2, 3.5])
```

```output
6.5
```

## Common operations

Since floats are numbers, we can perform math and comparison operations on them just as we do with ints.

### Math operations

Common math operations such as `+`, `-`, `*`, `/`, and `**` on floats are straightforward, and they always produce a float as a result. I will not give examples for these.

However, unlike ints, we do not perform integer and modulo divisions on floats. Technically, we can still perform these operations on floats, but they do not make any mathematical sense.

### Comparison operations

We can compare two floats, and the result will be a Boolean, just like what we can do with ints.

## When uses float?

We use floats whenever it makes sense to represent some real-valued data such as wage, income, profit, temperature, population density, etc.

```python
# Your wage
wage = 25.5
```

```python
# Your boss raises the wage by 50%
wage = wage * 1.5
```

```python
# Your new wage
wage
```

```output
38.25
```

## Conversion to float

We can convert a value to `float` using the `float()` function. However, not every value can be converted to `float`; only those considered "compatible" (just like in the case of ints). Let's see some examples.

### From Booleans

When converting a bool to float, `True` will produce `1.0` and `False` will produce `0.0`.

```python
float(True)
```

```output
1.0
```

```python
float(False)
```

```output
0.0
```

### From ints

When converting an int to float, the value technically stays the same; only the type is changed.

```python
float(10)
```

```output
10.0
```

### From strings

When converting a string to float, the string must "look like" a real number.

```python
# No problem
float("10.5")
```

```output
10.5
```

```python
# Negative sign is interpreted correctly
float("-10.5")
```

```output
-10.5
```

```python
# Leading and trailing spaces are ignored
float("   15.1   ")
```

```output
15.1
```

```python
# Error because of the comma (,) character
float("1,000.5")
```

```output
ValueError: could not convert string to float: '1,000.5'
```
