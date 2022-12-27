---
title: Tuples
---

## Introduction

The `tuple` type is the next sequence type we are going to learn. Tuples are almost identical to lists, except that they are immutable. It means that tuples cannot change once created and thus they don't have in-place operations.

## Create a tuple
To create a tuple, we put elements inside a pair of parentheses separated by commas.

```python
x = (1, 2, 3, 4)
print(x)
print(type(x))
```
```output
(1, 2, 3, 4)
<class 'tuple'>
```
If a tuple has only one element, we need to provide an extra comma. If not, Python will understand it as the integer `1` wrapped by parentheses.

```python
x = (1,)
print(x)
print(type(x))
```
```output
(1,)
<class 'tuple'>
```
The parentheses are optional.

```python
x = 1, 2, 3, 4
print(x)
print(type(x))
```
```output
(1, 2, 3, 4)
<class 'tuple'>
```
If you have too many elements to fit on one line, you arrange them in multiple lines.

```python
x = ("Apple", "Banana", "Orange", "Peach",
     "Guava", "Watermelon", "Pineapple")

print(x)
print(type(x))
```
```output
('Apple', 'Banana', 'Orange', 'Peach', 'Guava', 'Watermelon', 'Pineapple')
<class 'tuple'>
```
## Indexing and slicing tuples
Indexing and slicing tuples work the same way as they do with lists (because they are all of type sequence). However, since tuples are immutable, we only have read indexing and read slicing.

First, we create a tuple.

```python
x = (1, 2, 3, 4, 5)
x
```

```output
(1, 2, 3, 4, 5)
```


### Indexing

```python
# First element
x[0]
```

```output
1
```

```python
# Third element
x[2]
```

```output
3
```

```python
# Last element
x[-1]
```

```output
5
```


### Slicing

```python
# First 3 elements
x[:3]
```

```output
(1, 2, 3)
```

```python
# Last 3 elements
x[-3:]
```

```output
(3, 4, 5)
```

```python
# Second to fourth elements
x[1:4]
```

```output
(2, 3, 4)
```

```python
# From beginning to end with step 2
x[::2]
```

```output
(1, 3, 5)
```

```python
# Also no out-of-range error for slicing
x[1:1000]
```

```output
(2, 3, 4, 5)
```


## Nested tuples
Same as with lists, a tuple can contain other iterables including lists and tuples.

```python
# Create a nested tuple
x = (1, 2, (3, 4), [5, 6])
x
```

```output
(1, 2, (3, 4), [5, 6])
```

```python
# Access third element
x[2]
```

```output
(3, 4)
```

```python
# Access the first element of the third element
x[2][0]
```

```output
3
```


## Tuple iteration
Same as lists, we can use a `for` loop to iterate through a tuple.

```python
# Creat a tuple
x = (1, 2, 3, 4, 5)
```

```python
# Print out squares of elements of x
for e in x:
    print(e**2)
```
```output
1
4
9
16
25
```
## Mutability
Tuples are immutable, meaning that they cannot change once created. Each element of a tuple hold a reference to an object, and that reference stays the same forever.

You cannot reassign a new value to an element of the tuple `x`. For example, running `x[0] = 100` will produces an error.

```text
TypeError: 'tuple' object does not support item assignment
```

However, if one of the elements of `x` is of mutable type (e.g., a list), then we can still modify that mutable object. Let's consider an example.

```python
# Create a tuple containing a list
x = (1, 2, [3, 4])
print(x)
print(type(x))
```
```output
(1, 2, [3, 4])
<class 'tuple'>
```

```python
# See the ID of each element of x
for e in x:
    print(id(e))
```
```output
2151585048880
2151585048912
2151665796864
```

```python
# Now change the first element of 
# the inner list to 99 and double check
# (This is possible because lists are mutable)
x[-1][0] = 99
print(x)
```
```output
(1, 2, [99, 4])
```
You might think that the tuple `x` has changed, but it has not. Tuples are immutable, and `x` still holds the same references to the old underlying objects. What has happened is that the underlying object (the inner list in this case) has changed, not the tuple `x`. We can verify it by printing out the IDs of the elements of `x`.

```python
# IDs stay the same
for e in x:
    print(id(e))
```
```output
2151585048880
2151585048912
2151665796864
```
## Operations on tuples
Since tuples are immutable, we don't have in-place operations. Apart from that, we have all the regular operations that lists have. See [Lists (part 2)] for more details.

## Unpack tuples
Unpacking tuples works the same as it does with lists.

```python
# Create a tuple containing info about date
my_date = (2022, 4, 1)
my_date
```

```output
(2022, 4, 1)
```

```python
# Unpack all elements
y, m, d = my_date
print(y, m, d)
```
```output
2022 4 1
```

```python
# Get date and month only
_, m, d = my_date
print(m, d)
```
```output
4 1
```

```python
# Get year only
y, *_ = my_date
print(y)
2022
```
```output
2022
```

```output
2022
```

```python
# Get date only
*_, d = my_date
print(d)
```
```output
1
```
## Enumeration
When iterating through a sequence, we might want to access not only the elements but also their indexes. If so, we can use the function `enumerate()`

```python
# Create a tuple
runners = ("John", "Tom", "Harry")
runners
```

```output
('John', 'Tom', 'Harry')
```


Without `enumerate()`, we can only access the elements.

```python
for r in runners:
    print(r)
```
```output
John
Tom
Harry
```
With `enumerate()`, in each iteration, Python will return a two-element tuple: the first element is the index and the second element will be the value. 

```python
for r in enumerate(runners):
    print(r)
```
```output
(0, 'John')
(1, 'Tom')
(2, 'Harry')
```
Thus, we can write something like this.

```python
for r in enumerate(runners):
    print(f"{r[1]} is ranked {r[0] + 1}")
```
```output
John is ranked 1
Tom is ranked 2
Harry is ranked 3
```
However, if the returned tuple at each iteration, the code will be more intuitive.

```python
for i, runner in enumerate(runners):
    print(f"{runner} is ranked {i + 1}")
```
```output
John is ranked 1
Tom is ranked 2
Harry is ranked 3
```

