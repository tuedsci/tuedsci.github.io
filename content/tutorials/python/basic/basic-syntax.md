---
title: Basic syntax
---

This lesson aims to provide just some very basic syntax so that you can get started immediately. It's like when you first learn a new language: you don't dive into learning grammar right away; instead, you learn some basic vocabulary and simple sentences. This lesson serves such a purpose. In the next lessons, you will learn Python in a more systematic way.

## Math

Basic math operations such as addition, subtraction, multiplication, and division are straightforward.

Addition

```python
2 + 3
```

```output
5
```

Subtraction

```python
2 - 3
```

```output
-1
```

Multiplication

```python
2 * 3
```

```output
6
```

Division

```python
2 / 3
```

```output
0.6666666666666666
```

For integers, we can have integer division (to get the quotient) and modulus (to get the remainder).

Integer division

```python
2 // 3
```

```output
0
```

Modulus

```python
2 % 3
```

```output
2
```

Exponentiation in Python is `**`, not `^`.

```python
2 ** 3
```

```output
8
```

For more complicated expressions, use parentheses to specify the order of computation.

```python
1000 * (1 + 0.05) ** 20
```

```output
2653.2977051444223
```

## Assignments

We will learn about assignments in more detail later. For now, an assignment assigns a value to a variable. After the assignment, we can use the variable name to refer to its associated value. The general syntax for an assignment is as follows.

```python
variable_name = value
```

The following code assigns a value `3000` to the variable `profit`.

```python
profit = 3000
```

Now we can use `profit` instead of `3000`, for example, increase profit by 20%.

```python
profit * 1.2
```

```output
3600.0
```

Or divide `profit` in half

```python
profit / 2
```

```output
1500.0
```

## Literals

A literal is a fixed or constant value. When you see it, it is literally the value it represents, and no additional conversion is needed.

We can have literals of different types such as integers, real numbers, text strings, and so on. Data types will be discussed in detail in the next lessons.

An integer literal

```python
1000
```

```output
1000
```

A real literal

```python
3.14
```

```output
3.14
```

A Boolean literal

```python
True
```

```output
True
```

A string literal

```python
"Hello"
```

```output
'Hello'
```

Note that string literals must be wrapped in a pair of single or double quotes. Otherwise, Python will understand them as variable names. Specifically, `"Hello"` is a string literal, but `Hello` is a variable name.

## Expressions

An expression is anything that can be evaluated as a value and is usually formed by combining literals and variables using operators. Take a look at some examples.

Add two numbers

```python
2 + 3
```

```output
5
```

Concatenate two strings

```python
"Tue" + "Nguyen"
```

```output
'TueNguyen'
```

Double `profit`

```python
profit * 2
```

```output
6000
```

## Comments

Comments are used to document your code so that other people can understand what you have done (if your code is not so obvious). Other people also include future you because it is not uncommon that you will forget what you have done after a few weeks (or even days).

Comments are for humans only and are ignored by the interpreter. In Python, a comment starts with a `#`.

```python
# Increase profit by 50%
profit * 1.5
```

```output
4500.0
```

For a long comment, we can break it into multiple lines and start each line with a `#`. This is called a multi-line comment (obviously).

```python
# This stupid comment spans
# more than one line
# and I don't know why
# I am writing this
print("Surprised?")
```

```output
Surprised?
```

## Printing

You can use the `print()` function to print out things. We will learn about functions in detail later, but for now, all you need is an intuitive notion. Roughly speaking, a function takes some input (inside the parentheses), does something with the input, and spits out some output.

Here, the `print()` function takes an input, which could be a literal, a variable, or an expression. It then evaluates the associated value and prints out this value. Finally, it returns a `None` to indicate that it has done the job (but you can safely ignore this detail for now). Let's take a look at some examples.

Print a string literal

```python
print("Buongiorno")
```

```output
Buongiorno
```

Print a variable

```python
print(profit)
```

```output
3000
```

Print an expression

```python
print(profit * 2)
```

```output
6000
```

## Statements

A statement is a complete instruction that Python can execute. It is like a full sentence in English.

An assignment statement

```python
age = 20
```

A print statement

```python
print(age)
```

```output
20
```

However `age =` is not a statement, and you will get a syntax error when trying to run it.

In addition, if you come from a language like C/C++ or Java, you might be tempted to put a semicolon (i.e., `;`) at the end of a statement. But as Pythonistas, we don't do that. Just hit Enter and the statement ends.

```python
# You can use ; to write multiple statements on 1 line
# But this practice is discouraged
x = 5; y = 6; z = 7;
print(x + y + z)
```

```output
18
```

```python
# Write each statement on its own line
# This is better
x = 5
y = 6
z = 7

print(x + y + z)
```

```output
18
```

## Line continuation

On some occasions, you might have to write a complex statement, and keeping everything in one line make it very ugly and hard to read. If so, you can break it into multiple (shorter) lines in two ways

- Method 1: put a backslash `\` at the end of each line
- Method 2: wrap your code in a pair of parentheses

None of them is better than the other. It's just a matter of your preferences.

```python
# Method 1: use \
total = 1 + 2 + 3 +\
    4 + 5 + 6 +\
    7 + 8 + 9

print(total)
```

```output
45
```

```python
# Method 2: use ()
total = (1 + 2 + 3 +
    4 + 5 + 6 +
    7 + 8 + 9)

print(total)
```

```output
45
```

## White spaces

White spaces include spaces, tabs, and new-line characters. Often, whitespaces are ignored by Python's interpreter.

In the following example, extra spaces don't count. However, the last line is considered the best in terms of coding style.

```python
print(2+3)
print(    2 +     3)
print(2 + 3)
```

```output
5
5
5
```

Similarly, the two following code snippets are identical concerning results and performance. But the second snippet has a better coding style.

```python
# Snippet 1 (ugly)
x = 2 + 3


y = 4 + 5

print(x + y)
```

```output
14
```

```python
# Snippet 2 (beautiful)
x = 2 + 3
y = 4 + 5
print(x + y)
```

```output
14
```

## Indentation

In many languages such as C/C++, Java, or R, curly brackets (i.e., `{}`) are used to determine code blocks. Not Python. Python determines code blocks using indentation, which makes source code more readable.

Indentation is the spaces at the beginning of each line. A common convention is to use four spaces for one level of indentation (you use another four for the next level and so on). For now, just remember the following.

- Never indent your code if you don't have a reason to do so.
- Always indent the new line after a statement that ends with `:` such as `if`, `else`, `for`, or `while`.

Let's take a look at an example.

```python
age = 30

if age > 20:
    print("Congrats. You can buy vodka")
    print("But don't get drunk")
else:
    print("Sorry. Enjoy your milk tea")
```

```output
Congrats. You can buy vodka
But don't get drunk
```

In the above example, we create a variable `age` and assign a value `30` to it. Then we check if `age` is greater than `20`. If yes, Python will execute the block under `if`. Otherwise, it will execute the block under `else`.

By using indentation, Python understands that two `print` statements under `if` belong to the same block, and both will be executed when the condition is true. That's why we see two lines printed out.

If you try to dedent the code as in the example below, you will get an error because `if` always expects an indented block below it.

```python
# Try this to see the error
age = 30

if age > 20:
print("Congrats. You can buy vodka")
print("But don't get drunk")
else:
    print("Sorry. Enjoy your milk tea")
```

## Getting help

You usually need help when you face things that 1) you don't know or 2) you know, but you forget the details. If you need help when learning Python, there are two common ways.

1. Consulting Python's internal documentation
1. Googling

### Using Python documentation

We use `?` to see the documentation for Python objects such as variables, functions, classes, or modules. Let's take a look at some examples.

You read the code from someone else and see `abs()`. You wonder what it is. Try this.

```python
?abs
```

You know the `sorted()` function allows you to sort a list in descending order, but you forgot the detail. Try this.

```python
?sorted
```

### Googling

Let's say you want to sort a list in descending order in Python but don't know how. You can ask Google with a query like `How to sort a list in descending order in Python`.

But here is the better query (in my opinion) `python sort list descending order stackoverflow`.

First, we need correct keywords, not correct grammar. So don't bother spending time writing grammatically correct search queries. Search engines are smart; they know what you mean.

Second, StackOverflow is a very good source of reference for common issues related to coding. You often save a lot of time by looking for solutions from it, and the top-rated solutions are usually excellent. Try this as you learn Python and I am sure you will be convinced. The following formula will save your life many times.

> python + keywords for your problem + stackoverflow

## Summary

Again, I feel that I should summarize this wall of text into some bullet points so that you won't get lost.

**Math**

- Basic operations: `+`, `-`, `*`, `/`
- Integer division: `//`
- Modulus: `%`
- Exponentiation: `**`
- Use parentheses if needed

**Assignments**

- Syntax: `variable_name = value`

**Literals**

- Literals are fixed values
- Integer literals: `-5`, `0`, `3000`
- Real literals: `1.5`, `2.7`, `3.14`
- Boolean literals: `True`, `False`
- String literals: `"Hello"`
- Note that `"Hello"` is a literal, but `Hello` is not

**Expressions**

- An expression is anything that can be evaluated as a value
- Example: `10 * 5`, `profit / 2`

**Comments**

- Comments are used to document code and are ignored by the interpreter
- Start a comment with `#`
- Comments can be single-line or multiple-line

**Printing**

- Use `print()` to print literals, variables, or expressions

**Statements**

- A statement is a complete instruction that Python can execute
- Some best practices when writing Python statements
  - Write each statement on 1 line
  - Never end a statement with `;`

**Line continuation**

- Line continuation helps break a long statement into smaller pieces to increase readability
- We can use `\` or `()`

**Indentation**

- Python use indentation to determine code blocks
- Remember
  - Never indent your code for no reason
  - Always indent the new line after a statement that ends with `:`

**Getting help**

- We can get help in 2 ways
  - Use `?` to consult Python's documentation
  - Google with the following template `python + keywords + stackoverflow`
