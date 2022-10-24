---
title: From Jupyter Notebook to webpage
date: 2022-10-21
---

This post will guide you through the process of converting your existing jupyter notebook to a publishable webpage that can be embedded into your website. This guide is intended for Hugo websites, but the content is
still valid if you use a different static site generator.

<!--more-->

The overall process will be as follows.

1. Write a Jupyter Notebook with code cells and Markdown cells.
2. Use Nbconvert to convert your notebook into Markdown format.
3. Copy the generated Markdown file to your website.

## Nbconvert

### Installation

```bash
pip install nbconvert
```

### Basic use

First, we need to be inside the folder where the target notebook resides.

```bash
cd <nb-dir>
```

Then we can start converting it into the format we want with the following syntax.

```bash
jupyter nbconvert <nb-name> --to <format> --template <tmpl-name>
```

Suppose we want to convert a notebook named `my_analysis.ipynb` to different output formats using a template named `my_tmpl`, then the following is the syntax for each kind of output.

HTML output

```bash
jupyter nbconvert my_analysis.ipynb --to html --template my_tmpl
```

Markdown output

```bash
jupyter nbconvert my_analysis.ipynb --to markdown --template my_tmpl
```

## Custom output template

In this section, I will only show how to make a customized Markdown output template. But the process is similar for other formats.

Step 1: navigate to the templates folder.

- The templates folder is at `<python-root>/share/jupyter/nbconvert/templates/`
  .
- This is where all the default and custom templates are located.

Step 2: create a folder for your custom Markdown output template

- Duplicate the `markdown/` folder because we will extend from this template. Rename it the duplicated folder to `custommd/` (if you cannot think of any better name).
- Navigate into `custommd/`, open `index.md.j2`, and overwrite it with the structure you desire. The following code example (from [Nbconvert website](https://nbconvert.readthedocs.io/en/latest/customizing.html#a-practical-example)) extends the default Markdown template to wrap outputs in code fences with name `output`.

````text
{% extends 'markdown/index.md.j2' %}

{%- block traceback_line -%}
```output
{{ line.rstrip() | strip_ansi }}
```
{%- endblock traceback_line -%}

{%- block stream -%}
```output
{{ output.text.rstrip() }}
```
{%- endblock stream -%}

{%- block data_text scoped -%}
```output
{{ output.data['text/plain'].rstrip() }}
```
{%- endblock data_text -%}
````

Step 3: generate a Markdown output using the new template

```bash
jupyter nbconvert my_analysis.ipynb --to markdown --template custommd
```

Note: for more details about template customization,
visit [Nbconvert's official documentation](https://buildmedia.readthedocs.org/media/pdf/nbconvert/latest/nbconvert.pdf)

## My recommended workflow

Step 1: make a custom Markdown output template as mentioned earlier

Step 2: organize your notebooks into folders  
Notebooks belong to different topics should be in different folders

Step 3: create a dedicated notebook for converting other notebooks  
You can name it `md_convert.ipynb`, which contains a single cell like this.

```python
# Notebooks to convert
to_convert = ["my_analysis"]

# Output format and template
out_format = "markdown"
out_template = "custommd"

# Conversion process
import subprocess

for item in to_convert:
    filename = f"{item}.ipynb"
    args = ["jupyter", "nbconvert", filename, "--to", out_format]
    if out_template:
        args.extend(["--template", out_template])

    # Add this to generate base64 images
    args.append("--ExtractOutputPreprocessor.enabled=False")

    # Execute
    subprocess.run(args)
```

However, the current version of `nbconvert` will auto-generate tables in form of HTML tags together with an inline style, something like this.

```html
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
```

Thus, we need to do extra work to remove this inline style so that the tables will be rendered with a style consistent with the whole website.

For now, I cannot think of any better solution except to add another cell `md_convert.ipynb` with the following content.

```python
# Remove the generated styles
import re

for item in to_convert:
    filename = f"{item}.md"

    # Read the generated Markdown contents
    with open(filename) as f:
        contents = f.read()

    # Remove style
    stripped = re.sub("<style scoped>.*</style>\n", "", contents,
                      flags=re.DOTALL)

    # Overwrite the original Markdown file
    with open(filename, "w") as f:
        f.write(stripped)
```

Basically, the above code just reads the generated markdown, cleans the text between `<style scoped>` and `</style>`, and finally overwrites the stripped content back to the original Markdown file.

Step 4: copy the Markdown file generated in step 3 to the `content/` folder of your website and let Hugo do the build.
