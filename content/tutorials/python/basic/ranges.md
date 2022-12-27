---
title: Ranges
---

## Introduction
A range is an immutable sequence of evenly-spaced integers. We often use the `range` type to quickly make a sequence of integers to iterate through such as in a `for` loop.

## Create a range
We use the `range()` function to create a range object. There are three syntax variations as follows.

- `range(stop)`
- `range(start, stop)`
- `range(start, stop, step)`

The general rule is similar to that of a typical python slice.

- `start` is included
- `stop` is excluded
- `step` specifies the gap between each jump

Let's see some examples.

### `range(stop)`

For this syntax, `start=0` and `step=1` by default. As a result, you will get a consecutive range of integers that starts from `0` and ends at `stop - 1`. Let's try to create one.

```python
r = range(5)
```

Its type is `range` as expected.

```python
type(r)
```

```output
range
```


However, if you print it, you don't see its elements (more on that later).

```python
print(r)
```
```output
range(0, 5)
```
To see the elements it will eventually generate when being used in a `for` loop, for example, you can cast it to a list or a tuple.

```python
list(r)
```

```output
[0, 1, 2, 3, 4]
```


Now you can use range to quickly write some code such as printing out the squares of the first 5 integers starting from `0`.

```python
for i in range(5):
    print(i ** 2)
```
```output
0
1
4
9
16
```
### `range(start, stop)`

If you want to start at some value different from `0` but still keep `step=1`, then you can use the syntax `range(start, stop)`. For example, printing out the squares of the first 5 integers starting from `1`.

```python
for i in range(1, 6):
    print(i ** 2)
```
```output
1
4
9
16
25
```
### `range(start, stop, step)`
In case you want the gap between jumps different from `1`, you can use the syntax `range(start, stop, step)`. For example, printing out the first 5 even integers starting from `0`.

```python
for i in range(0, 9, 2):
    print(i)
```
```output
0
2
4
6
8
```
You can use negative `step` to jump backward, but in this case, you have to set `start > stop`.

```python
list(range(5, 0, -1))
```

```output
[5, 4, 3, 2, 1]
```


If `start < stop` while `step` is negative, you will get an empty range.

```python
list(range(0, 5, -1))
```

```output
[]
```


## Why use ranges?

There are two main reasons to use ranges. First, it makes writing code more convenient. Second, it optimizes memory usage. 

The first reason is obvious as you have seen from the examples so far. Using `range(10)` is much quicker and less prone to error than manually typing `[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]`.

For the second reason, a range doesn't contain actual elements. It is like a rule for generating elements instead of a container containing those elements. 

Basically, `range(5)` is similar as the tuple `(0, 1, 2, 3, 4)`. However, the elements are not generated immediately but only when asked. For example, when you iterate through a range in a `for` loop, each element will be generated on-the-fly and then destroyed immediately at the end of the iteration. 

Thus, there is no difference in memory usage when you iterate through a range of size 1 million versus size 10. In contrast, if you use a tuple to store such 1 million integers, you have to use 1 million times more memory.

It is also the second reason that when you print out a range, you don't see its elements printed out.

## More examples

### Cumulative sums
Suppose we want to compute the sum of the first `n` integers starting from `1` to `n`.

```python
n = 50
total = 0

for i in range(1, n + 1):
    total += i
    
print(total)
```
```output
1275
```
Now suppose we want to compute the sum of the first 50 even integers starting from `2`.

```python
n = 50
total = 0

for i in range(2, 2*n + 1, 2):
    total += i

print(total)
```
```output
2550
```
### Factorials

Suppose we want to compute `n! = 1.2...n`.

```python
n = 6
fact = 1

for i in range(2, n + 1):
    fact *= i
    
print(fact)
```
```output
720
```
