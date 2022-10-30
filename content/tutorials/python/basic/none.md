---
title: None
---

## Introduction
As briefly discussed in the previous lesson, Python uses the keyword `None` to denote the concept of null (i.e., nothing). The data type of `None` is `NoneType`.

```python
type(None)
```

```output
NoneType
```

Note that if you evaluate `None` on a Python console or a Jupyter cell, you will see nothing. To force print it out, you have to use the `print()` function.

```python
# You will see no output
None
```

```python
# You will see None printed out
print(None)
```


```output
None
```

## Domain
The domain of `NoneType` consists of a unique value, which is `None`. There is only a single instance of `None` in your program. If you try to assign it to different variables, all these variables will refer to this unique `None` as shown in the example below.

```python
x = None
y = None
x is y
```

```output
True
```

## How to get None?
### From the literal None
The easiest way to get a `None` is through an assignment with the keyword `None`.

```python
x = None
```

```python
print(x)
```
```output
None
```

```python
type(x)
```

```output
NoneType
```

### From a functional call
We sometimes call a function to perform some action, and when the action is done, the function usually returns something. For example, the `abs()` function takes a number as input and returns its absolute value.

```python
x = abs(-5)
```

Here the `abs()` function computes the absolute value of `-5` and returns the result to where it is called, i.e., the RHS of the assignment. Thus, the assignment is equivalent to `x = 5`, and we can easily verify that.

```python
x
```

```output
5
```

However, some functions are designed to just do something without returning anything. For example, the `print()` function takes an input and just prints it out for visual purposes. For such functions, a convention is to return `None` to indicate that the function effectively produces no output for subsequent uses.

```python
x = print("Hello")
```

```output
Hello
```

Here you see `Hello` printed out because it is what the `print()` function is designed for. It is not what `print()` returns. In fact, `print()` returns `None`, and the assignment is equivalent to `x = None`. Again, we can easily verify that.

```python
print(x)
```

```output
None
```

In some cases, a function returns `None` to indicate something special. However, you can safely ignore this for now. We will revisit it when we learn about functions.


## Common operations
There is not much we can do with `NoneType` because it is so simple. The most commonly used operation is to check if a variable is actually `None`. To do this, we perform an identity comparison using the keyword `is`. 

```python
# Create two variables
x = None
y = 10
```

```python
# Check if x is None
x is None
```

```output
True
```

```python
# Check if y is None
y is None
```

```output
False
```

To check if a variable is not `None`, we use `is not`.

```python
x is not None
```

```output
False
```

```python
y is not None
```

```output
True
```

Note that we can also use `==` instead of `is` to check if a variable is `None`. However, it is not recommended because as mentioned earlier, there is only one `None`. Thus, from a philosophical point of view, it makes more sense to use identity comparison instead of value comparison. In addition, identity comparison is faster.

