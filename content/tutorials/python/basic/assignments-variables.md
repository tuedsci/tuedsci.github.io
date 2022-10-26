---
title: Assignments and variables
---


From the last lesson, we know that a variable (or variable name) is created through an assignment. For example, `x = 1000` will create a variable named `x` and assign the value `1000` to it. However, this description makes people think that variable `x` is like a container that stores the value `1000`. This is not true, and you will know why in this lesson.

## Assignments demystified

Let's consider a simple assignment.

```python
x = 1000
```

This assignment is not as simple as it looks. Here is what happened under the hood.

Step 1: the equality sign divides the assignment into two parts: the left-hand side (LHS) and the right-hand side (RHS). Python always evaluates the RHS first to come up with a **value**. Here, the RHS is just an integer literal, so the value is literally `1000`.

Step 2: Python creates an **object** to store the value `1000`. This object occupies a real slot in the memory of your PC.

Step 3: Python looks into a look-up table that contains all **variable** names and sees no name `x` in it. Thus, Python creates a name `x` in this look-up table.

Step 4: finally, Python establishes a **binding** (or mapping) between variable `x` (in step 3) and the object (in step 2) and records that association into the look-up table.

Thus, a variable is just a label, and it does not contain anything. It is an object that contains a value.

I think the following analogy would help.

- Your PC's memory is like an array of lockers
- An object is like a box
- Creating an object is like putting a box inside a locker
- The value associated with the object is what is stored inside the box
- A variable is the label pasted on the box

Thus, the assignment `x = 1000` can be seen as

1. Create a box (object) to hold a gift (value `1000`)
1. Put the box inside a locker (a slot in memory)
1. Paste a label (variable) on the box so that we know where to retrieve it later

Every assignment, simple or complicated, works the same way as described above.

Let's take a look at another example.

```python
x * 2
```

```output
2000
```

Here is what happened.

Step 1: Python evaluates the expression and realizes not everything is a literal. Here, `x` is a variable.

Step 2: to proceed, Python must interpret what is the value associated with `x`. So it goes to the look-up table, looks for the name `x`, and finds the object (box) associated with it.

Step 3: Python opens the box and gets the value `1000`. Now, this is a literal, and Python can use it in the multiplication expression. As a result, we see `2000` printed out.

## Why variables?

It is extremely complicated for us, as human beings, to deal with objects directly. So we use variables to help abstract away all unnecessary technical complications so that we can focus on solving our main problem at a higher level.

## Object IDs

Every object, when created, has a unique ID, that stays with the object until it dies (just like the ID number of a person). However, as mentioned earlier, we rarely work with objects directly. Thus, to check the ID of an object, we must work with the variable associated with it. Specifically, we use `id(x)` to get the ID of the object that `x` refers to.

```python
id(x)
```

```output
2248410640944
```

Let's try another assignment.

```python
y = 1000
```

When we access `y`, we will get `1000` back, and nothing mysterious about this.

```python
y
```

```output
1000
```

But does this value `1000` has anything to do with the other value `1000` associated with `x`? Or more specifically, do `x` and `y` refer to the same underlying object? The answer is no.

We can verify this by printing out the IDs of the objects associated with `x` and `y`.

```python
print(id(x))
print(id(y))
```

```output
2248410640944
2248410640688
```

You see, although both `x` and `y` are associated with the same value `1000`, they are pointing to two different objects. Think of this situation as having two 50-euro notes. These notes have the same value but are distinct notes (with different serial numbers). Or if you prefer the "box model", here we have two boxes containing the same thing. But they are distinct boxes, and `x` is a label pasted on one box while `y` is a label pasted on the other.

## Value and identity comparison

I hope now you can distinguish three related concepts: variables, objects, and values. Of those three, we care only about values because values are the data containing useful information to us. However, data or values cannot stand on their own. They need to be materialized by means of objects. We, as humans, do not work with objects directly but through means of variables. Thus, when we say two things are equal, we must be clear about the subjects of comparison.

Python use the double-equality sign (i.e., `==`) for **comparing values** and the keyword `is` for **comparing identities**. So `x == y` will return `True` if the associated values with `x` and `y` are equal, even if `x` and `y` are pointing to different objects. In contrast, `x is y` will return `True` only if `x` and `y` is pointing to the same underlying object.

In terms of the "box model", `x == y` returns `True` when the two boxes contain the same thing. They could be (but not necessarily) the same box. While `x is y` only returns `True` when `x` and `y` are two labels pasted on the same box.

Let's take a look at some examples.

First, we run two assignments and print their values.

```python
x = 1000
y = 1000

print(x)
print(y)
```

```output
1000
1000
```

To check if the values of `x` and `y` are the same, we use value comparison with the double-equality sign.

```python
x == y
```

```output
True
```

As you can see, they are equal in terms of values.

To check if `x` and `y` are actually referring to the same underlying objects, we use identity comparison with the keyword `is`.

```python
x is y
```

```output
False
```

The result is `False` because `x` and `y` are pointing to two distinct objects with different IDs as shown below.

```python
print(id(x))
print(id(y))
```

```output
2663125676400
2663125673904
```

Why different IDs? Because in the first assignment, Python evaluates the RHS, comes up with the value `1000`, and creates an object to hold that value. Python then links that object to variable `x`. In the second assignment, Python evaluates RHS and also comes up with the value `1000`, but this time it creates a new object to hold that value.

## Garbage collection

Let's say you want to associate `x` with a different value, for example, `5000`. You can simply run the following assignment.

```python
x = 5000
```

You check the value associated with `x` again, and it has been indeed changed to `5000`.

```python
x
```

```output
5000
```

But you know that there was an object created to hold that value. The one with the following ID.

```python
id(x)
```

```output
2625447588144
```

So what happened with the old object that holds value `1000` and the binding between it and variable `x`?

It turns out that when you re-assign a new value to an existing variable, Python immediately deletes the old binding, establishes a new one, and updates this new binding into the look-up table. It is like peeling the label on the old box and pasting it on the new box.

In addition, since the old binding is deleted, there is no way to access the old object (remember we only get access to an object through the variable associated with it, but now that association is gone). The old object is considered "garbage", and it is not good for your PC's memory.

Fortunately, Python is equipped with something called auto-garbage collection. When Python sees an object with no reference (a box with no label), it will summon the garbage collector to destroy that object and release memory to the system for future assignments.

## Aliasing

Consider the following assignments.

```python
x = 1000
y = x
```

The first assignment works just as described earlier. Python evaluates the RHS and gets the value `1000`, then a box is created to hold that value, and finally, the label `x` is pasted on the box.

However, the second assignment is a bit tricky. When there is only a variable on the RHS, Python will not evaluate anything. It just establishes a new binding between `y` and the object that `x` is currently referring to. Now both `x` and `y` are pointing to the same object (like two labels pasted on the same box). This is called **aliasing**. `x` and `y` are just nicknames (or aliases) of the same thing.

You can easily verify this as follows.

```python
print(id(x))
print(id(y))
print(x is y)
```

```output
2625447586928
2625447586928
True
```

## Python interning

We have seen how the "assignment theory" works for some large numbers such as `1000`, `2000`, or `5000`. Let's see if the theory is still true with "small numbers".

```python
x = 100
y = 100
```

If what I have told you before is true, there should be two distinct objects created although the values they hold are the same, i.e., `100`. Eh, not this time.

```python
print(id(x))
print(id(y))
print(x is y)
```

```output
2625363971408
2625363971408
True
```

As you can see, `x` and `y` are pointing to the same object, and it is not consistent with the theory. This weird behavior (called **Python interning**) is a result of some "optimization decision" made by Python's core development team. I will not discuss it in detail, but the idea is that, for a thing that is used frequently, it is not optimal to make many duplications of it. One possible solution is just maintaining a single copy and all the references will be pointed to this copy. This will help save memory and make comparisons a lot faster. That's exactly what Python's core development team did. They accepted this language inconsistency in exchange for performance.

### Integer interning

For some reason, the core development teams decided that those between `-5` and `128` are in the "interning range". However, depending on specific implementations, the range might vary. These integers are used much more frequently than others, so at startup, Python loads and caches them in memory. Whenever you try to assign a value in this range to a variable, Python will point the variable to the corresponding cached copy instead of creating a new object.

Let's try some examples to verify this for integers within the "interning range".

```python
x = -5
y = -5
print(x is y)
```

```output
True
```

```python
x = 256
y = 256
print(x is y)
```

```output
True
```

But for integers outside the "interning range", things go back to conform to the standard "assignment theory" as in the following examples.

```python
x = -6
y = -6
print(x is y)
```

```output
False
```

```python
x = 257
y = 257
print(x is y)
```

```output
False
```

### String interning

Python interning happens not only to "small integers" but also to some strings (not all). Usually (meaning not always), a string that consists of only letters, digits, and underscores will get interned.

Let's take a look at some examples.

```python
x = "hello_world"
y = "hello_world"
x is y
```

```output
True
```

```python
x = "hello world"
y = "hello world"
x is y
```

```output
False
```

## Takeaway

Usually, you can safely use Python without the knowledge of interning because you also rarely perform identity comparisons in practice. However, I believe it is useful to have an awareness of such weird behavior and the reasons for its existence. For the most part, the standard "assignment theory" works just fine, and that's all you need.
