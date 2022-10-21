--- 
title: Set up Katex for Hugo website
date: 2022-10-18
math: true
---

Math formulas can be rendered beautifully by using third-party JavaScript
libraries such as [Katex](https://katex.org/)
or [MathJax](https://www.mathjax.org/). In this post, I will show you how to
incorporate Katex into your Hugo website. The reason I chose Katex is that it
is faster while still has all the functionalities I need.

<!--more-->

## Set up

Step 1: create a partial for Katex at `layouts/partials/katex.html` and fill it
with the following content

```html

<link rel="stylesheet"
      href="https://cdn.jsdelivr.net/npm/katex@0.16.2/dist/katex.min.css"
      integrity="sha384-bYdxxUwYipFNohQlHt0bjN/LCpueqWz13HufFEV1SUatKs1cm4L6fFgCi1jT643X"
      crossorigin="anonymous">

<script defer src="https://cdn.jsdelivr.net/npm/katex@0.16.2/dist/katex.min.js"
        integrity="sha384-Qsn9KnoKISj6dI8g7p1HBlNpVx0I8p1SvlwOldgi3IorMle61nQy4zEahWYtljaz"
        crossorigin="anonymous"></script>

<script defer
        src="https://cdn.jsdelivr.net/npm/katex@0.16.2/dist/contrib/auto-render.min.js"
        integrity="sha384-+VBxd3r6XgURycqtZ117nYw44OOcIax56Z4dCRWbxyPt0Koah1uHoK0o4+/RRE05"
        crossorigin="anonymous"
        onload="renderMathInElement(document.body);"></script>

<script>
    document.addEventListener("DOMContentLoaded", function () {
        renderMathInElement(document.body, {
            delimiters: [
                {left: "$$", right: "$$", display: true},
                {left: "$", right: "$", display: false}
            ]
        });
    });
</script>
```

Note: for the latest version, please
visit [here](https://katex.org/docs/browser.html)

Step 2: include this partial to the `<head>` section
of `layouts/_default/baseof.html`

```html

<head>
    ...
    {{ if .Params.math }}{{ partial "katex.html" . }}{{ end }}
    ...
</head>
```

## Config your posts

To enable Katex rendering, you should set `math: true` in the front matter of
your post.

```yaml
# your-post.md
title: Your post title
math: true
```

Then in your post, use `$` for inline Latex and `$$` for block Latex.

To enable Katex globally, set `math: true` in your website config.

```yaml
# config.yaml
params:
  math: true
```

## Demo

Here is an example of inline Latex $E = mc^2$.

Here is an example of block Latex.

$$
\varphi = 1+\frac{1} {1+\frac{1} {1+\frac{1} {1+\cdots} } }
$$
