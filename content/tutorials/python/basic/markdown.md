---
title: Introduction to Markdown
math: true
---

## What is Markdown?

Markdown is a lightweight markup language designed to work with a plain-text editor. Think of it as a simplified version of Microsoft Word. Markdown allows you to quickly add simple formatting elements to to your texts such as

- Headings
- Lists
- Text emphases
- Links
- Images

Originally designed for technical documentation in 2004, Markdown is now used widely in many areas such as blogging, online forums, technical writing, and even book publishing.

Fact: this tutorial series was completed exclusively in Markdown.

## Why use Markdown?

### Versatility

Markdown can be used for many purposes such as

- Technical documentation
- Notes and books
- Static site generation

### Minimal distraction

Markdown offers much fewer features compared to rich-text text processors such as Microsoft Word. But this turns out to be its main advantage. By restricting you to a small set of formatting options, Markdown forces you to fucus on writing good content rather than spending time tweaking the appearances such as themes, fonts, colors, etc.

### Portability

Unlike a Word file (`.docx`), a Markdown file (`.md`) is just a simple plain text file, which can be opened by any free text editors such as Notepad++, Sublime Text, or Atom.

- You won't have to stick with any proprietary software or worry when migrating your files to different operating systems or cloud services because you can always access their contents
- You can use version control to effectively keep track of changes to your files

### Easy integration

If you plan to be a data analyst/scientist/researcher, technical documentation is part of your daily work. Markdown makes your life much easier by allowing you to mix your technical notes and executable code in the same place, a notebook for example.

### Easy conversion

You can easily convert a Markdown file to different formats such as Latex, slides, PDF, or HTML.

## Basic Markdown syntax

### Headings

We use headings to organize contents into sections. They are available from `h1` to `h6`, with `h1` being the largest and `h6` being the smallest.

There should be only one `h1` heading in your whole file, which is the title of the document. Other sections will begin from `h2`. Moreover, you should never use beyond `h3` because nesting your contents too deep make it hard to follow.

In Mardown, we use `#` to generate headings. The number of `#`'s indicates the level. Try the each of the following line in your notebook to see the result.

```markdown
# Level 1

## Level 2
### Level 3
#### Level 4
##### Level 5
###### Level 6
```

### Paragraphs

Two paragraphs are separated by a blank line. One common mistake is to think that a new line will start a new paragraph.

This is the wrong way to make paragraphs.

```markdown
Paragraph 1
Paragraph 2
```

This is the correct way to make paragraphs.

```markdown
Paragraph 1

Paragraph 2
```

If you want to start a new line after another line but don't want a huge blank line between the two, you must put TWO spaces at the end of the first line.

### Lists

List can be either ordered or unordered. Items in an ordered list are consecutive numbers, while items in an unordered list are just bullet points.

To make an ordered list, put `1. ` in front of each list item as follows.

```markdown
1. Item 1
1. Item 2
1. Item 3
```

You will see something like this.

1. Item 1
1. Item 2
1. Item 3

To make an unordered list, put `- ` in front of each list item as follows.

```markdown
- Item 1
- Item 2
- Item 3
```

You will see something like this.

- Item 1
- Item 2
- Item 3

Lists can also be nested into multiple levels. However, try to keep them as shallow as possible (remember Zen of Python: "Flat is better then nested").

Here is a nested unordered list.

```markdown
- Item 1
  - Sub-item 1.1
  - Sub-item 1.2
- Item 2
  - Sub-item 2.1
  - Sub-item 2.2
```

You will see something like this.

- Item 1
  - Sub-item 1.1
  - Sub-item 1.2
- Item 2
  - Sub-item 2.1
  - Sub-item 2.2

Here is a nested ordered list.

```markdown
1. Item 1
   1. Sub-item 1.1
   1. Sub-item 1.2
1. Item 2
   1. Sub-item 2.1
   1. Sub-item 2.2
```

You will see something like this.

1. Item 1
   1. Sub-item 1.1
   1. Sub-item 1.2
1. Item 2
   1. Sub-item 2.1
   1. Sub-item 2.2

Here is a nested mixed list.

```markdown
1. Item 1
   - Sub-item 1.1
   - Sub-item 1.2
1. Item 2
   - Sub-item 2.1
   - Sub-item 2.2
```

You will see something like this.

1. Item 1
   - Sub-item 1.1
   - Sub-item 1.2
1. Item 2
   - Sub-item 2.1
   - Sub-item 2.2

### Text emphases

Text emphases are straighforward.

- `**Bold**` will make **Bold**
- `*Italic*` will make _Italic_
- `***Bold and italic***` will make **_Bold and italic_**
- `~~Strike through~~` will make ~~Strike through~~

### Code fences

Code fences are used to emphasize texts that should be understood as code elements, for example, variable names, expressions, or code blocks. There are two types of code fences: inline and block.

Inline code fences are used for short code elements. The elements are embedded within regular texts (thus the name inline). To make an inline code, wrap the element inside a single backtick (i.e., `` ` ``). Here are some examples.

- `` `profit` `` will be rendered as `profit`
- `` `price * 1.1` `` will be rendered as `price * 1.1`

In contrast, block code fences are used for, well, blocks of code, which normally spans more than one line. To make a block code, wrap the code inside a triple backticks (i.e., ` ``` `). You can also specify the language of the code to take advantage of syntax highlighting.

Here is an example.

````markdown
```python
def say_hi(name):
    print(f"Hello {name}")
    print("Have a good day")
```
````

You will see something like this.

```python
def say_hi(name):
    print(f"Hello {name}")
    print("Have a good day")
```

### Latex

Markdown supports Latex syntax so you can type math formulas easily. Similar to code fences, there are inline (`$`) and block (`$$`) Latex.

Here is an example of inline Latex.

```markdown
$f(x) = {n \choose x} p^{x} (1-p)^{n-x}$ is the PMF for binominal distribution.
```

You will see something like this.

$f(x) = {n \choose x} p^{x} (1-p)^{n-x}$ is the PMF for binominal distribution.

Here is an example for block Latex.

```markdown
$$
M = \begin{bmatrix}a_1 & b_1 \\
a_2 & b_2 \\
a_3 & b_3
\end{bmatrix}
$$
```

You will see something like this.

$$
M = \begin{bmatrix}a_1 & b_1\\
a_2 & b_2 \\
a_3 & b_3
\end{bmatrix}
$$

### Links

You can embed a link into your document as follows `![Caption](link/to/source)`.

Here is an example.

```markdown
If you don't know something, ask [Google](https://www.google.com)
```

You will see something like this.

If you don't know something, ask [Google](https://www.google.com)

### Blockquotes

Block quotes are used for quotes or excerpts. You start a blockquote with a `>`.

Here is an example.

```markdown
> My advice to you is to get married: if you find a good wife you’ll be happy; if not, you’ll become a philosopher (Socrates)
```

You will see something like this.

> My advice to you is to get married: if you find a good wife you’ll be happy; if not, you’ll become a philosopher (Socrates)

For multi-paragraph blockquotes, insert a blank line between paragraphs and remember to start every line with a `>` as in the following example.

```markdown
> My advice to you is to get married: if you find a good wife you’ll be happy; if not, you’ll become a philosopher (Socrates)
>
> Behind every great man is a woman rolling her eyes (Jim Carrey)
```

You will see something like this.

> My advice to you is to get married: if you find a good wife you’ll be happy; if not, you’ll become a philosopher (Socrates)
>
> Behind every great man is a woman rolling her eyes (Jim Carrey)

### Images

To insert an image, use the following syntax ![Caption](path/to/image).

Here is an example.

```markdown
![Python logo](https://upload.wikimedia.org/wikipedia/commons/c/c3/Python-logo-notext.svg)
```

You will see something like this.

![Python logo](https://upload.wikimedia.org/wikipedia/commons/c/c3/Python-logo-notext.svg)

### Tables

Complicated animals like tables can still be generated using Markdown as shown in the example below.

```markdown
| id  | name       | email             |
| :-- | :--------- | :---------------- |
| 3   | Tue Nguyen | tuedsci@gmail.com |
| 1   | John Doe   | john@gmail.com    |
| 2   | Jane Smith | jane@hotmail.com  |
```

You will see a very nice table like this.

| id  | name       | email             |
| :-- | :--------- | :---------------- |
| 3   | Tue Nguyen | tuedsci@gmail.com |
| 1   | John Doe   | john@gmail.com    |
| 2   | Jane Smith | jane@hotmail.com  |

However, my advice is not to type tables by yourself (you can still try it if you want). Instead, go to some website that offers a free Markdown table generator such as [this one](https://www.tablesgenerator.com/markdown_tables). Another option is to look for pluggins that do such jobs for the editor of your choice. For example, I use some Markdown Table Formatter add-on on Sublime Text, and it works very well so far.

### Final notes

The syntax introduced so far is enough for you to have a nice-looking notebook. I rarely use any Markdown features beyond those.

> Remember, the most important thing is the quality of your analysis. Don't bother too much with fancy formatting

## Summary

I think it's good to summarize this lengthy lesson in a few lines (not really, but much more compact than this whole wall of text) so that you can grab the essence.

**Headings**

```markdown
# Level 1
## Level 2
### Level 3
#### Level 4
##### Level 5
###### Level 6
```

**Emphasis**

```markdown
Bold: **bold**
Italic: _italic_
Bold and italic: **_Bold and italic_**
Strike through: ~~Strike through~~
```

**Unordered lists**

```markdown
- item 1
- item 2
- item 3
```

**Ordered lists**

```markdown
1. item 1
1. item 2
1. item 3
```

**Nested lists**

```markdown
- item 1
  - sub-item 1.1
  - sub-item 1.2
- item 2
  - sub-item 2.1
  - sub-item 2.2
```

**Mixed nested lists**

```markdown
1. item 1
   - sub-item 1.1
   - sub-item 1.2
1. item 2
   - sub-item 2.1
   - sub-item 2.2
```

**Inline code**

```markdown
`42`, `profile`, `x + 5`
```

**Block code**

````markdown
```python
def say_hi(name):
    print(f"Hello {name}")
    print("Have a good day")
```
````

**Inline Latex**

```markdown
$E = mc^2$
```

**Block Latex**

```
$$
M = \begin{bmatrix}a_1 & b_1 \\
a_2 & b_2 \\
a_3 & b_3
\end{bmatrix}
$$
```

**Links**

```markdown
[Google](https://www.google.com)
```

**Single-paragraph quotes**

```markdown
> This is a quote
```

**Multi-paragraph quotes**

```markdown
> This is the first paragraph
>
> This is the second paragraph
```

**Images**

```markdown
![Caption](path/to/image)
```

**Tables**

```markdown
| id  | name       | email             |
| :-- | :--------- | :---------------- |
| 3   | Tue Nguyen | tuedsci@gmail.com |
| 1   | John Doe   | john@gmail.com    |
| 2   | Jane Smith | jane@hotmail.com  |
```
