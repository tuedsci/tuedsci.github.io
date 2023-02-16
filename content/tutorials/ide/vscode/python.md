---
title: Python
---

## Install a Python interpreter

You need a Python interpreter to run a Python program. Thus, make sure that Python is already installed on your machine. You can check this by running `python --version` on a terminal.

## Choose an interpreter

Whenever you open a file with the extension `.py` (Python file) or `.ipynb` (Jupyter Notebook file), VS Code will immediately scan for a Python interpreter available on your machine so that you can execute the code. If there are multiple interpreters, VS Code will ask you to choose one. You will see the information of the interpreter chosen in the Status Bar.

If you want to switch to another interpreter, there are two ways.

1. Click on the current interpreter in the Status Bar and select a new one
1. Open the Command Palette and search for the keyword `python interpreter`

## Set up Python extensions

### Microsoft Python extension

To have the best experience working with Python in VS Code, you should install the [Python extension](https://marketplace.visualstudio.com/items?itemName=ms-python.python) by Microsoft. This extension provides extensive support for Python, including syntax highlighting, code suggestion and completion, code linting and formatting, debugging, Jupyter notebooks, etc.

### Select a linter

There are various extensions for Python linting such as `Flake8`, `pylint`, or `mypy`. I simply use `pylint`, which is the default linter of VS Code. You can select a linter via the Command Palette by searching the keywords `python select linter`.

### Black formatter

While a linter tries to detect the potential problems in your code, a formatter tries to fix them. I recommend using [Black Formatter](https://marketplace.visualstudio.com/items?itemName=ms-python.black-formatter). To set up Black properly, follow the below steps.

1. Install the Black Formatter extension from VS Code marketplace
1. Install the `black` module for Python with `pip install black`
1. Configure Black Formatter in `setting.json` (see the note below)

**Note**: You need set Black as your Python formatter in `settings.json` as follows.

```json
{
  "python.formatting.provider": "black"
}
```

However, it is likely that you have already set Prettier as the default code formatter as follows.

```json
{
  "editor.defaultFormatter": "esbenp.prettier-vscode"
}
```

This will prevent Black from working, and since Prettier does not support Python, you cannot format your Python code. To fix this, you need to overwrite the formatter for Python as follows.

```json
{
  "[python]": {
    "editor.defaultFormatter": "ms-python.black-formatter"
  }
}
```

### Other useful extensions

- [isort](https://marketplace.visualstudio.com/items?itemName=ms-python.isort&ssr=false#review-details)

### Other notes

Sometimes, you define a long dictionary and want it to appear like this.

```python
person = {
  "name": "Tue",
  "country": "Vietnam",
  "edu": ["BS", "MS"]
}
```

However, Black will format the code like this.

```python
person = {"name": "Tue", "country": "Vietnam", "edu": ["BS", "MS"]}
```

To avoid this, you can add a "magic comma" after the last item as in the code snippet below, and Black will keep each element on a separate line.

```python
person = {
  "name": "Tue",
  "country": "Vietnam",
  "edu": ["BS", "MS"],
}
```

This trick works for any kind of iterable including dictionaries, lists, tuples, or sets.

## Jupyter Notebooks

### Create a notebook

You can create a Jupyter notebook in two ways.

1. Create a new file with the extension `.ipynb`
1. Open the Command Palette and search for the keyword `new jupyter`

### Format a notebook

To format a code cell, put the cursor at the cell and hit `Ctrl + Alt + F`. You might need to remap the keybinding if it is not working for the first time.

To format the whole notebook, put the cursor at any cell, then right-click and choose `Format Notebook` from the context menu.

### Outline

Headings created in a notebook will generate the outline, which is shown in the Outline section of the Sidebar in Explorer. It works the same as the outline of a Markdown file.

### Variable Explorer

When you click on the Variables button at the top bar of a notebook, the Variable Explorer will show up in the Panel, listing all the variables in the current session. You can click on the pop-out icon on the left of the variable name (if available) to open it in the Data Viewer for more details and operations. It is especially helpful when working with complicated data structures such as Pandas data frames.

### Plots

When hovering on a plot, you will see several options on the top right that allow you to copy, save, or open the plot in the Plot Viewer.

### Export

As of now, VS Code allows you to export your notebooks to several output formats, including PDF, HTML, and `.py` files. For PDF, you need to install [TeX](https://nbconvert.readthedocs.io/en/latest/install.html#installing-tex).
