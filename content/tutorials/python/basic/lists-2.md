---
title: Lists (part 2)
---

## Nested lists
A nested list is a list that contains other lists.

```python
# Create a nested list
x = [[1, 2, 3, 4], [5, 6]]

# View
x
```

```output
[[1, 2, 3, 4], [5, 6]]
```


Here we create a nested list `x` with two elements, each of which is in turn a list.

```python
# First element of x
x[0]
```

```output
[1, 2, 3, 4]
```

```python
# Second element of x
x[1]
```

```output
[5, 6]
```


Since `x[0]` is a list, we can access its element using slice and indexing.

```python
# First element of x[0]
x[0][0]
```

```output
1
```

```python
# Last element of x[0]
x[0][-1]
```

```output
4
```

```python
# First 2 elements of x[0]
x[0][:3]
```

```output
[1, 2, 3]
```

```python
# Replace last element of x[0] by 'A'
x[0][-1] = "A"
```

```python
# View the updated content
x
```

```output
[[1, 2, 3, 'A'], [5, 6]]
```


## List iteration

We can iterate through a list using a `for` loop. We will learn about loops in more detail in the "Control flows" section, but for now, you just need some basic understanding.

As you will see later, collection types such as lists, tuples, sets, or dictionaries are called **iterable** because we can iterate through using a loop. Each time we visit an element of the collection is called an **iteration**. Let's take a look at some examples.

First, we create a list.

```python
x = [1, 2, 3, 4, 5]
```

If we want to print the square of each element of `x`, we can do it as follows.

```python
print(x[0] ** 2)
print(x[1] ** 2)
print(x[2] ** 2)
print(x[3] ** 2)
print(x[4] ** 2)
```
```output
1
4
9
16
25
```
But that is not a good solution for two reasons. First, we have to repeat similar codes many times; and second, we have to keep track of how many items are in the list. Imagine what happens if the list has 1000 elements. A better solution is to use a `for` loop as shown below.

```python
for e in x:
    print(e ** 2)
```
```output
1
4
9
16
25
```
Here, we iterate through each element of the list (from left to right), and we can decide what we want to do in each iteration in the code block under `for`. Recall that the new line after `:` must be indented one tab to indicate that the code belongs to the `for` loop. This code block defines the logic that will be applied to each element of `x` through a proxy variable `e`. Each time an element of `x` is visited, it is assigned to variable `e` so that we can keep a clean, minimal code.

If you are still not clear, here is a more concrete description of the above example.

- In the first iteration, `e` was assigned the first element of `x`, which is `1`. Thus, `print(e ** 2)` prints out `1`.
- After this iteration, Python notices that it has NOT reached the end of the list, so it moves to the next iteration.
- In the second iteration, `e` is assigned the second element of `x`, which was `2`. Thus, `print(e ** 2)` prints out `4`.
- This logic happens again and again until the fifth iteration is finished. This time, Python notices that it already reaches the end of the list, and the loop ends.

## More examples of list iteration

### Indentation matters

First, we create a list.

```python
x = [1, 2, 3, 4, 5]
```

Now consider two code snippets.

```python
# Snippet 1
for e in x:
    sq = e ** 2
    print(sq)
```
```output
1
4
9
16
25
```

```python
# Snippet 2
for e in x:
    sq = e ** 2
print(sq)
```
```output
25
```
In snippet 1, both assignment and print statements are indented, so both belong to the `for` loop and are executed in every iteration. As a result, you see the square of each element of `x` printed out.

In snippet 2, only the assignment is indented, so it is executed five times. However, since the print statement is not indented, nothing is printed out although `sq` changes its value in each iteration. When the last iteration is completed, `sq` assumes the value `25`.  After the `for` ends, Python moves to the next part of the program and executes the print statement and you see `25` printed out.

### Be careful with loop variables

The variable `e` in the above examples is called a **loop variable**, and you should think of it as a temporary variable to get access to each element of the iterable being iterated. You don't have to name it `e`. In fact, you can use whatever name you want such as `i`, `j`, or `element`. However, remember to use the same name both in the `for` statement and within the code block under the loop.

Let's take a look at an example.

```python
for i in x:
    print(e ** 2)
```
```output
25
25
25
25
25
```
Here, Python still iterates through all the elements of `x` using `i` as the loop variable. In each iteration, `i` indeed takes the value of the corresponding element of `x`. 
However, we mistakenly use `e ** 2` instead of `i ** 2` in the code block under the `for` loop, and from the last example, we know that `e` takes the value `5`. That's why we see `25` printed out `5` times.

### Filtering values

We can use the `for` loop together with `if` to filter the values satisfying certain conditions from a collection.

```python
# Create a list of numbers
x = [1, 2, -7, 8, -9, -4, 10, 30]
```

```python
# Print out only positive elements
for e in x:
    if e > 0:
        print(e)
```
```output
1
2
8
10
30
```

```python
# Print out only even elements
for e in x:
    if e % 2 == 0:
        print(e)
```
```output
2
8
-4
10
30
```

```python
# Print out only positive and even elements
for e in x:
    if (e > 0) and (e % 2 == 0):
        print(e)
```
```output
2
8
10
30
```
### Counting values

Suppose we have a list of scores of students and want to count how many students pass the exam. Suppose we have a list of scores and suppose the passing score is `4` (out of `10`).

```python
# Set up
scores = [1, 2, 3, 7, 9, 10, 10]
threshold = 4
```

We will record the number of passes in variable `num_passed`, which is initialized to `0`. As we iterate through each score, we compare the score to `threshold` and decide if it is a passing or a failing one. If it is a pass, we increase `num_passed` by `1` because we indeed see a student that passes the exam. Otherwise, we do nothing and move to the next iteration. The idea is implemented as follows.

```python
# Counting
num_passed = 0
for s in scores:
    if s > threshold:
        num_passed = num_passed + 1
```

```python
# Check the results
num_passed
```

```output
4
```

The result is correct because only the last four students pass the exam.

## Operations on a list

We distinguish between two types of operations on a list: regular and in-place. Regular operations operate on lists and return some results but do not change the original lists. In contrast, in-place operations modify the original lists.

### Regular operations

First, we create a list.

```python
x = [1, 2, 3, 1, 1, 2, 7, 5]
x
```

```output
[1, 2, 3, 1, 1, 2, 7, 5]
```


#### Number of elements

We use the function `len()` to count the number of elements of a list.

```python
# How many elements are in x?
len(x)
```

```output
8
```


#### Membership checking

We use the `in` operator to check if some value is in a list. The result will be a Boolean `True` or `False`.

```python
# Is 1 in x?
1 in x
```

```output
True
```

```python
# Is 100 in x?
100 in x
```

```output
False
```


#### Number of occurrences

We use the method `.count()` to count the number of occurrences of a value in a list.

```python
# How many 1's in x
x.count(1)
```

```output
3
```


#### Concatenation

We use the `+` operator to concatenate 2 lists and get a bigger list.

```python
[1, 2, 3] + ["A", "B"]
```

```output
[1, 2, 3, 'A', 'B']
```


#### Replication

We use `*` operator to replicate a list

```python
# Replicate a list twice
[1, 2, 3] * 2
```

```output
[1, 2, 3, 1, 2, 3]
```

```python
# Quickly create a list of ten zeroes
[0] * 10
```

```output
[0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
```


#### Sorting

We use the function `sorted()` to sort a list (if its elements can be compared)

```python
# Sort x in ascending order
sorted(x)
```

```output
[1, 1, 1, 2, 2, 3, 5, 7]
```

```python
# Sort x in descending order
sorted(x, reverse=True)
```

```output
[7, 5, 3, 2, 2, 1, 1, 1]
```


However, if you run `sorted([1, 2, "A"])`, you will get an error because Python cannot compare integers and strings.

#### Reversing

We can reverse a list using slicing in a Pythonic way.

```python
x[::-1]
```

```output
[5, 7, 2, 1, 1, 3, 2, 1]
```


We can find the index of the first occurrence of a value in a list using method `.index()`.

```python
# Index of the first value of 2 in x
x.index(2)
```

```output
1
```

```python
# Index of first value of 5
x.index(5)
```

```output
7
```


However, if the element is not in the list, for example, `100`, trying to run `x.index(100)` will produce an error `ValueError: 100 is not in list`.

### In-place operations
These operations make some changes to a list, and the change is saved to the original list. After that, a `None` is usually returned to indicate that the action is done correctly.

First, we create a list.

```python
x = [2, 7, -3, 11.5, 2]
x
```

```output
[2, 7, -3, 11.5, 2]
```


#### Sorting

We use method `.sort()` to sort a list and save this change to the original list instead of returning a sorted version as we have with the function `sorted()`.

```python
# Sort a list and save the change
# You don't see anything printed out 
# because a None is returned
x.sort()
```

```python
# Check if x is indeed modified
x
```

```output
[-3, 2, 2, 7, 11.5]
```


To verify that a `None` is indeed returned, we assign the output of `x.sort()` to a dummy variable.

```python
z = x.sort()
print(z)
```
```output
None
```
To in-place sort a list in descending order, we set `reverse=True`

```python
x.sort(reverse=True)
print(x)
```
```output
[11.5, 7, 2, 2, -3]
```
#### Reversing
To in-place reverse a list, we use the method `.reverse()`.

```python
x = [1, 2, 3] # Original list
x.reverse() # In-place reverse
print(x) # Double check
```
```output
[3, 2, 1]
```
#### Appending
We use the method `.append()` to add a single element to the end of a list.

```python
x = [1, 2, 3] # Original list
x.append(99) # Add 99 to the end of x
print(x) # Double check
```
```output
[1, 2, 3, 99]
```
#### Extending
We use the method `.extend()` to add multiple elements to the end of a list.

```python
x = [1, 2, 3] # Original list
x.extend([88, 99]) # Add 88 and 99 to the end of x
print(x) # Double check
```
```output
[1, 2, 3, 88, 99]
```
#### Insertion
We use the method `.insert()` to insert a new element into a list at a specified index.

```python
x = [1, 2, 3] # Original list
x.insert(1, "A") # Insert "A" into the 2nd position (index=1)
print(x) # Double check
```
```output
[1, 'A', 2, 3]
```
#### Removal
We use the method `.remove()` to remove a value from a list. If the value is not in the list, you will get an error. If there are multiple occurrences of the value in the list, only the first one is removed.

```python
x = [1, 2, 3, 1] # Original list
x.remove(1) # Remove the value 1
print(x) # Verify that only the first value of 1 is removed
```
```output
[2, 3, 1]
```
#### Deletion
We use the keyword `del` to delete an element of a list by its index.

```python
x = [1, 2, 3] # Original list
del x[-1] # Delete the last element
print(x) # Double check
```
```output
[1, 2]
```

## Mutability
Python lists are mutable, meaning that they can change their contents during their time. The opposite of mutable is **immutable**. All the scalar types introduced so far (`NoneType`, `bool`, `int`, `float`) are immutable.

Mutability is a property of an object, not of a variable. When an object is created, it has a specific data type that stays with it forever. That data type determines whether the object is mutable or immutable. A variable is just a label being pasted on an object that can be either mutable or immutable. Let's see some examples.


```python
# First, we assign 1000 to x
x = 1000
print(x)
print(id(x))
print(type(x))
```
```output
1000
1636460889840
<class 'int'>
```
After the above assignment, `x` is associated with an immutable object of type `int`. Now run the following assignment to reassign a list to `x`.


```python
# Now we reassign [1, 2, 3] to x
x = [1, 2, 3]
print(x)
print(id(x))
print(type(x))
```
```output
[1, 2, 3]
1636460868736
<class 'list'>
```
Some people see that `x` has "changed" from `1000` to `[1, 2, 3]` and think that `x` is mutable. This is wrong because the assignment just changes the binding between the variable `x` (a label) from one object to another object with a different ID.

Now try to append an element to `x` (more precisely, to the object `x` is pointing to, which is a list)


```python
x.append(4)
print(x)
print(id(x))
```
```output
[1, 2, 3, 4]
1636460868736
```
As you can see, `x` has been updated with a new element, but its ID hasn't changed. That's what it means to be mutable. The underlying object can mutate (in this case, expanding to accommodate a new element).

In contrast, an immutable object is like a box that is fixed: It cannot expand or shrink. Once created, it stays the same until being destroyed by the garbage collector. And don't be confused between mutability and the reassignment of variables.

> Mutability is the property of objects, not of variables!



## Unpack a list

Suppose we have a list that contains information about date.

```python
my_date = [2022, 4, 1]
my_date
```

```output
[2022, 4, 1]
```


Suppose from `my_date`, we want to extract the year, month, and date into three separate variables. Here is the "traditional" way to do it.

```python
y = my_date[0]
m = my_date[1]
d = my_date[2]
```

There is nothing wrong with this, but in Python, we can do it in a more succinct way by unpacking.

```python
# Unpack each element in my_date into 
# into the corresponding variable in the LHS
y, m, d = my_date

# Double check
print(y)
print(m)
print(d)
```
```output
2022
4
1
```
Sometimes, we just want to extract some elements and ignore the others. We can use `_` for the unwanted variables so that we don’t have to waste time thinking names for them.

```python
# Get date and month only and ignore year
_, m, d = my_date
print(m)
print(d)
```
```output
4
1
```

```python
# Get year only
y, *_ = my_date
print(y)
```
```output
2022
```