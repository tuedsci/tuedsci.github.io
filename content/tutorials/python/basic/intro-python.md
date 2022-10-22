---
title: Introduction to Python
---

## What is Python?

> Python is a general-purpose, interpreted, interactive, muti-paradigm, and
> high-level programming language.

Ugh, this sounds like a mouthful, but let's break down what each of these terms actually means.

### General-purpose

Programming languages can be divided into general-purpose or domain-specific.

General-purpose languages are those designed to solve many classes of problems in different domains. Take Python, for example, we can find its applications in many areas including (but not limited to) data science, scientific computing, web development, game development, graphical user interface, embedded systems,
and more. Other common general-purpose languages include Java, Julia, C, C++, etc.

On the other hand, domain-specific languages are intended to solve problems within a small set of specific domains. For example, SQL is designed primarily to work with relational databases. Similarly, MATLAB is mainly used for vector and matrix computations to solve scientific and engineering problems. Or R is rarely used outside the realm of statistical and data analysis. Some might even raise an eyebrow if you call these programming languages.

### Interpreted

Programming languages are also classified as compiled or interpreted, depending on how a program of the language is executed.

In a (fully) compiled language, such as C, Rust, or Go, the source code (the instructions you write) is first compiled into the machine code of your targeted computer by a compiler. Then this complied machine code is executed by the CPU.

Things are different in interpreted languages. Your source code is executed directly by an interpreter without being compiled into machine code (roughly speaking). Python, R, and JavaScript belong to this category.

Generally speaking, a program written in an interpreted language often runs slower than its counterpart written in a fully compiled language. However, the gain from the reduced development time usually outweighs the limitation in computation speed. Moreover, for data-intensive tasks in which speed is an important factor, there are many third-party packages that are blazingly fast. For example, NumPy is fully written C and supports very fast numerical computation. Pandas, another popular package for data science, is built on top of NumPy, and thus inherits this strength.

### Interactive

Being an interpreted language means that you can work with Python in an interactive mode (or style). This means you just need to write some lines of code, run them, and immediately see the results. This instant feedback makes Python an excellent tool for exploratory tasks commonly found in data science.

### Multi-paradigm

A programming paradigm is an approach to solving problems using a programming language. The major paradigms include imperative, logical, functional, and object-oriented. I will not discuss them here because it is out of the scope of this series, but you can easily find plenty of online resources if you are interested in knowing more.

It is shown that any given problem can be solved using one of those paradigms. However, depending on the nature of the problem, one paradigm might be more appropriate than the others. Python manages to support all of the four listed above, and that makes it a very powerful language.

### High-level

A programming language can be either high-level or low-level, depending on whether its syntax is closer to humans or to the machine.

A high-level language is human-friendly in that its syntax is very readable and straightforward for programmers to translate ideas into code. The downside is that it gives us less control over physical hardware.

In contrast, a low-level language is machine-oriented. You have to do more work in specifying the steps and operations for the machine, which make it harder and longer to write a program. The benefit is you have more fine-grained control over the hardware (but you have to be really careful as well).

Generally speaking, only assembly and machine code are considered low-level. The rest, including Python, R, Java, C, or C++, are considered high-level. However, low and high are relative, for example, Python is considered to be higher level than C.

## Brief history

Python was developed in 1989
by [Guido van Rossum](https://en.wikipedia.org/wiki/Guido_van_Rossum), a Dutch programmer. Guido first created Python as a hobby project because he had nothing interesting to do during Christmas as his office was closed (sounds like a typical geek). He then used it in some projects at his workplace and received very good feedback from his colleagues. In 1991, Guido decided to publish the code, officially making Python open-source.

## The name Python

There is a mystery about the name Python. If you look at the name and the logo, you might think it was inspired by a kind of snake. But the snake was completely irrelevant. In fact, Guido was a bit random when choosing the name for the language he had just created. He wanted something short and kind of
mysterious, and at the time he was a huge fan of [Monty Python's Flying Circus](https://it.wikipedia.org/wiki/Monty_Python%27s_Flying_Circus), a comedy show broadcast by BBC. And Guido was like "Why don't we just name it
Python and get rid of all the headache?"

## Python 2 or 3?

Since its first release in 1991, Python has gone through three major versions, namely Python 1, 2, and 3, of which only the last two are still in use.

Python 2 came out in 2000 with many enhancements compared to Python 1. It was the version that brought Python its widespread use and long-lasting fame. However, as time passed, Python 2 revealed some fatal weaknesses deemed "unfixable" (I will not discuss them here).

Python 3 is the next advancement after Python 2, and it was first released in 2008. It is not just an extension of Python 2 but a complete rebuild of the language. Its main intention was to fix all the critical shortcomings of the previous version. Python 3 did achieve that goal but at the cost of giving up backward compatibility. Backward incompatibility means that code written in Python 2 might not run on a Python 3 interpreter (and vice versa). However, for the large part, the syntaxes are almost identical in both versions.

As a side note, Python 2 was [officially sunset](https://www.python.org/doc/sunset-python-2/) on January 1, 2020, meaning there will be no more improvement for this version (even if security problems are found and reported).

In short, use Python 3 whenever possible because it is better than Python 2 in every aspect, plus it has a future.
