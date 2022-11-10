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

We can use `for` loop together with `if` to filter the values satisfying certain conditions from a collection.

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


## Mutability
To be updated

## Copies of a list

## Operations on a list
### Regular operations

### Inplace operation

## Unpack a list

