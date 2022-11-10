---
title: Lists (part 1)
---

## Introduction

The `list` type is one of the 4 sequence types that we will learn in this series. The other three are `tuple`, `range`, and `str`. 

A sequence is an ordered collection of elements. Each element of the sequence can be accessed using the sequence name and the position (or index) of the element. Note that Python is zero-based indexing, meaning that it starts counting from `0`, not from `1`.

Since understanding lists is important for understanding other collection types, especially sequences, I will break this topic into two parts to keep the materials in reasonable lengths. This is the first part.

## Create a list
We create a list by listing its elements within a pair of square brackets (i.e., `[]`). The elements are separated by commas.


```python
# Create a list
x = [1, 2, 3, 4, 5]
```

```python
# View value of x
x
```

```output
[1, 2, 3, 4, 5]
```

```python
# View type of x
type(x)
```

```output
list
```

A list can hold elements of arbitrary types such as Booleans, ints, floats, strings, and even lists.

```python
# Create a list with elements of different types
y = [None, True, 1, 2.5, "ABC", [1, 2]]
```

```python
# View value of y
y
```

```output
[None, True, 1, 2.5, "ABC", [1, 2]]
```

```python
# View type of y
type(y)
```

```output
list
```


If there are too many elements in a list, you can arrange them in multiple lines as follows.

```python
# Arrange a long list
fruits = [
	"Apple", "Banana", "Orange", "Peach",
	"Guava", "Watermelon", "Pineapple"
]
```

## Index a list
Indexing means accessing a single element of a list by position. There are two types of list indexing: read and write.

- Read indexing: we access an element, read the value, and do not change it.
- Write indexing: we access an element and change it.

The general syntax for indexing a list is `list_name[index]`.

### Read indexing
First, we create a list.

```python
# Create a list
x = [1, 2, 3, 4, 5]

# View value of x
print(x)
```

```output
[1, 2, 3, 4, 5]
```

Python starts counting from `0`, so a list of `N` elements will be indexed by `0`, `1`, ..., and `N-1`.

```python
# First element (index: 0)
x[0]
```

```output
1
```

```python
# Third element (index: 2)
x[2]
```

```output
3
```

```python
# Last element (index: N - 1)
x[4]
```

```output
5
```


If you try to index beyond `N-1`, you will get an error as in the following example.

```python
x[5]
```

```output
IndexError: list index out of range
```

By default, a positive index means counting from left to right. However, you can provide a negative index, and Python will interpret it as counting from right to left.

```python
# Last element (index: -1)
x[-1]
```

```output
5
```

```python
# Second to last element (index: -2)
x[-2]
```

```output
4
```


### Write indexing

First, recall our list.

```python
x
```

```output
[1, 2, 3, 4, 5]
```


We can index an element and overwrite it with a new value using an assignment.

```python
# Change the first element to 99
x[0] = 99
```

```python
# View the updated content
x
```

```output
[99, 2, 3, 4, 5]
```


We can also index an element and delete it using the `del` keyword.

```python
# Delete the first element
del x[0]
```

```python
# View the updated content
x
```

```output
[2, 3, 4, 5]
```

## Slice a list

Unlike indexing, in which we access one element at a time, slicing means we access a bunch of elements (called a slice) simultaneously. However, like indexing, we also have two modes of slicing, which are read and write.

The general syntax for slicing a list `x` is `x[start:stop:step]`.

- `start`: the starting index (will be included in the result)
- `stop`: the ending index (will be excluded in the result)
- `step`: the step between each jump

In many cases, we want a consecutive slice (i.e., `step=1`). If so, we can use `x[start:stop]` instead.


### Read slicing

First, we create a list.

```python
# Create a list
x = [1, 2, 3, 4, 5]
```

To slice the first 3 elements we use the syntax `x[start:stop]` because we want a consecutive slice. With this syntax, we set
- `start=0` because we want to start at index `0`, and this element is included in the result.
- `stop=3` because we want to stop at index `2`, but since `stop` is excluded from the result, we have to set it to `3`.

```python
# First 3
x[0:3]
```

```output
[1, 2, 3]
```


We can omit `start` if we start indexing from the beginning of the list.

```python
# Another way to get the first 3
x[:3]
```

```output
[1, 2, 3]
```


Similarly, we can omit `stop` if we want to slice until the end of the list.

```python
# From 3rd to end
x[2:]
```

```output
[3, 4, 5]
```


If we omit both `start` and `stop`, we will get a slice from the beginning to the end of the list, which is a shallow copy of `x`. We will learn more about this in the next section.

```python
x[:]
```

```output
[1, 2, 3, 4, 5]
```


Unlike indexing, we will not get an error when slicing beyond `N`, in which case Python will slice until the end of the list.

```python
x[:10000]
```

```output
[1, 2, 3, 4, 5]
```


If `step=k` (for positive `k`), Python will skip `k-1` elements between each jump.

```python
# Slice from beginning to end 
# but skip 1 element between each jump
x[::2]
```

```output
[1, 3, 5]
```

```python
# Skip 2 elements between each jump
x[::3]
```

```output
[1, 4]
```


If we provide a negative `step`, Python will slice from right to left. In that case, `start` must be greater than `stop`. If not, we will get an empty slice.

```python
# 4th to 3nd
# (remember start is included, but stop is excluded)
x[3:1:-1]
```

```output
[4, 3]
```

```python
# Last to 2nd
x[:1:-1]
```

```output
[5, 4, 3]
```

```python
# Last to first (reverse the list)
x[::-1]
```

```output
[5, 4, 3, 2, 1]
```

```python
# When start < stop (while step is negative)
# we will get an empty slice
x[1:3:-1]
```

```output
[]
```


The following examples summarize recommended ways to slice a list.

```python
# First 3
x[:3]
```

```output
[1, 2, 3]
```

```python
# 2nd to 4th 
x[1:4]
```

```output
[2, 3, 4]
```

```python
# 2nd to last
x[1:]
```

```output
[2, 3, 4, 5]
```

```python
# Last 2
x[-2:]
```

```output
[4, 5]
```

```python
# Skip 1 element between each jump
x[::2]
```

```output
[1, 3, 5]
```

```python
# Get a shallow copy
x[:]
```

```output
[1, 2, 3, 4, 5]
```

```python
# Reverse a list
x[::-1]
```

```output
[5, 4, 3, 2, 1]
```

### Write slicing
Write slicing works in a similar fashing as write indexing: we slice part of a list and overwrite (i.e., update or delete) this part.

First, we create a list.

```python
# Create a list
x = [1, 2, 3, 4, 5]
```

We can replace the first three elements of `x` with new values such as `10, 20, 30`.

```python
# Replacement
x[:3] = [10, 20, 30]
```

```python
# View the updated content
x
```

```output
[10, 20, 30, 4, 5]
```


If the value on the RHS is longer (or shorter) than the slice on the LHS, the list will automatically expand (or shrink) accordingly.

```python
# Overwrite a slice and expand the list
x[:3] = ["A", "B", "C", "D"]
```

```python
# View the updated content
x
```

```output
['A', 'B', 'C', 'D', 4, 5]
```

```python
# Overwrite a slice and shrink the list
x[:3] = ["AA"]
```

```python
# View the updated content
x
```

```output
['AA', 'D', 4, 5]
```


We can also delete a slice of a list using the keyword `del`.

```python
# Delete first 2 elements
del x[:2]
```

```python
# View the updated content
x
```

```output
[4, 5]
```


## Summary
In this lesson, you know what lists are, how to create them, and how to index and slice them using modes namely read and write. In the next lesson, you will learn more advanced topics about lists, including nested lists, list iteration, mutability, and common operations in lists.