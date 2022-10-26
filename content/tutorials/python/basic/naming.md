---
title: Naming rules and conventions
---

> There are only two hard things in Computer Science: cache invalidation and naming things (Phil Karlton)

When writing a program, we often have to give names to many things such as variables, functions, classes, and modules. Therefore, it is crucial to learn the rules and conventions. **Rules** are specifications that we must follow, while **conventions** are more like suggestions of best practices by experienced programmers that are widely accepted by the community. We are not required to follow conventions, but we should.

For now, we only focus on naming variables. However, the rules and conventions are very similar (with some minor exceptions) to the others.

## Naming rules

A name in Python must satisfy the three following rules to be considered valid.

1. Only consists of characters from the three groups: digits (`0-9`), English letters (`a-zA-Z`), and underscores (`_`).
1. Does not start with a digit
1. Does not coincide with one of Python's reserved words.

Reserved words are words that have special meanings to Python. They are listed below, but you don't have to remember them for now. You will remember them as you progress.

```python
# List of Python's reserved words
False       class       finally     is          return
None        continue    for         lambda      try
True        def         from        nonlocal    while
and         del         global      not         with
as          elif        if          or          yield
assert      else        import      pass
break       except      in          raise
```

Besides, Python is **case-sensitive**, meaning that it distinguishes between lowercase and uppercase. Thus, `firstname`, First`Name, and ` are different names.

Here are some examples of valid names.

```python
# Valid names
age
num_jobs
file_name
_xyz
```

And here are examples of invalid names.

```python
# Invalid names
warnings!       # contains a special character !
net.profit      # contains a special character .
4oceans         # starts with a digit
break           # coincides with the break keyword
```

## Naming conventions

Here are some of the best practices you should follow when naming.

> 1. Always use lowercase

You should use `name` instead of `Name` or `NAME`. However, in some occasions such as when defining global constants, you can use all uppercase.

> 2. Use snake_case

In the `snake_case` convention, words are separated by underscores so that the name `looks_like_a_snake`.

Other languages might adopt different conventions. For example, C-style languages such as Java or JavaScript often follow `camelCase`, in which the first word is always in lowercase, but for each word followed, the first letter is capitalized. It is called `camelCase` because it `looksLikeACamelWithHumps`.

> 3. Exception: use PascalCase for classes

`PascalCase` is similar to `camelCase` except that the first letter of every word is capitalized. I don't know why it is called `PascalCase`, but definitely not because it looks like Pascal.

```python
# Good
class BankAccount:
    ...

# Bad
class bank_account:
    ...

# Also bad
class bankAccount:
    ...
```

> 4. Meaningful and easy to remember

Good code should be self-explanatory, and having good names is just one factor. Consider using `interest_rate` or at least `rate` instead of `r` or `ir`.

> 5. Reasonable length

Keep your name short and simple, but still meaningful (now you know what Phil Karlton really meant). Let's say you want a variable name for the sale of April. Use `sales_apr` instead of `sales_data_for_april`.

> 6. Avoid names of popular functions and modules

If you run `print = 5`, you will not be able to use the `print()` functions.

To conclude this section, here are some examples of names with good styles (following conventions) and bad styles (not following conventions).

```python
# Good
first_name
gross_profit
class_rank


# Bad
fn              # ambiguous
FirstName       # not snake case
print           # name of a popular function
os              # name of a popular module
sys             # name of a popular module
salary_data_of_10000_households     # too long
```
