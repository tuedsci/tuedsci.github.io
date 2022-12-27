---
title: Strings
---

## Introduction
A string is an immutable sequence of Unicode characters such as `"Hello"` or `"Python is fun"`. Python does not distinguish between characters and strings. There is only the string type, not the character type. A single character is a string of length 1.


## Create a string
To create a string, we typically wrap it in a pair of double quotes.

```python
s = "Hello"
print(s)
print(type(s))
```
```output
Hello
<class 'str'>
```
However, there are more ways for you to create a string in Python.

- Single quotes: `'hello'`
- Double quotes: `"hello"`
- Triple single quotes: `'''hello'''`
- Triple double quotes: `"""hello"""`

In general, they are the same. However, in some cases, using one might be more convenient than the others (more on this later).

First, to see that all types of quotes producing the same results, we will create 4 strings using 4 different ways and compare them.

```python
# Create 4 strings
s1 = 'hello'
s2 = "hello"
s3 = '''hello'''
s4 = """hello"""
```

```python
# Compare them
print(s1 == s2)
print(s1 == s3)
print(s1 == s4)
```
```output
True
True
True
```
We often use double quotes when our string contains single quotes.

```python
# Use double quotes 
# if your string contains single quotes
"He's a good man"
```

```output
"He's a good man"
```


You can still use single quotes in this case, but you need to escape the single quote inside the string using `\` character. If not, Python will interpret that quote as the ending quote, and the part `s a good man'` will not be part of the string. As a result, you will get an error.

```python
# This also works, but it's ugly
'He\'s a good man'
```

```output
"He's a good man"
```


Likewise, use single quotes if your string contains double quotes.

```python
'He said: "I am a good man"'
```

```output
'He said: "I am a good man"'
```


Triple quotes (both single triple and double triple) are often used for strings that span on multiple lines because they preserve the newline character (i.e., `"\n"`). They are very convenient for writing SQL queries.

```python
q = """
select
    name,
    address,
    email
    from employee
where 
    (salary >= 50000)
    and (country = 'UK')
"""
print(q)
```
```output

select
    name,
    address,
    email
    from employee
where 
    (salary >= 50000)
    and (country = 'UK')
```
## Indexing and slicing
Since a string is a sequence, the indexing and slicing work exactly as it does with lists or tuples. Each character is an element of the sequence.

First, we create a string.

```python
# Suppose you have a product code
code = "VN_20230102_ABCXYZ"
```

Indexing a string gives you a character, which is a string of length 1.

```python
# First character
code[0]
```

```output
'V'
```

```python
# 4th character
code[3]
```

```output
'2'
```

```python
# Last character
code[-1]
```

```output
'Z'
```


Slicing a string gives you a substring of the original one.

```python
# First 2 characters
code[:2]
```

```output
'VN'
```

```python
# Last 6 characters
code[-6:]
```

```output
'ABCXYZ'
```

```python
# 4th to 11th
code[3:11]
```

```output
'20230102'
```


## String iteration
Same as with lists or tuples, we can use a `for` loop to iterate through each character of a string.

```python
# Create a string
s = "Hello"

# Iterate through each character and print
for c in s:
    print(c)
```
```output
H
e
l
l
o
```
## Conversion to string
We use `str()` function to convert objects from other types to the string type.

Convert from `bool` to `str`.

```python
str(True)
```

```output
'True'
```

```python
str(False)
```

```output
'False'
```


Convert from `int` to `str`.

```python
str(10)
```

```output
'10'
```


Convert from `float` to `str`.

```python
str(2.5)
```

```output
'2.5'
```

```python
str(1.5e6)
```

```output
'1500000.0'
```


Convert from `list` to `str`.

```python
str([1,2,3])
```

```output
'[1, 2, 3]'
```


## Mutablity
Strings are immutable, meaning they cannot change once created. If `s` is a string, you will get an error when trying to modify it such as `s[0] = "B"`.

## Order of characters
Under the hood, each character is encoded by an integer. Thus, comparing characters is in fact comparing their underlying integer codes. According to Unicode

- Letters `A-Z` are encoded with integers `65-90`
- Letters `a-z` are encoded with integers `97-122`

We use `ord()` function to get the underlying code for a character.

```python
print(ord("A")) # 65
print(ord("Z")) # 90
print(ord("a")) # 97
print(ord("z")) # 122
```
```output
65
90
97
122
```
Thus, `A < B` but `a > B`. Let's see more examples.

```python
print("BOB" < "BILL") # False because O > I
print("MARK" < "MARY") # True because K < Y
print("Happy" < "beautiful") # True because H < b (not B)
```
```output
False
True
True
```
A good practice when comparing strings is to convert them to the same case (either lower or upper) first, then do the comparison.

The inverse function of `ord()` is `chr()`, which takes an integer as input and returns the corresponding character.

```python
print(chr(65)) # Letter A
print(chr(80)) # Letter P
print(chr(2000)) # Some weird character
```
```output
A
P
ߐ
```
## Operations on a string
Since strings are immutable sequences, we will have all regular operations as we do with tuples. In addition, we will have special operations for Unicode strings.

