---  
title: Syntax highlighting with highlight.js
date: 2022-10-20
---  

The `highlighting.js` library is a comprehensive project that offers a rich
collection of syntax highlighting styles (both dark and light themes). You can
easily incorporate it into your website with just three lines of code. This
post will walk you through all the steps as well as give some demos.

<!--more-->

## Setup

Step 1: open your `.html` layout file

Step 2: put the following code in the `<head></head>` section

```html

<link rel="stylesheet"
      href="//cdnjs.cloudflare.com/ajax/libs/highlight.js/11.6.0/styles/<style-name>.min.css">
<script src="//cdnjs.cloudflare.com/ajax/libs/highlight.js/11.6.0/highlight.min.js"></script>
<script>hljs.highlightAll();</script>
```

Note: you should visit [here](https://highlightjs.org/download/) to get the
latest version

Step 3: take a look at the demo [here](https://highlightjs.org/static/demo/) to
choose the want you like the most

Step 4: go to
the [official GitHub repo](https://github.com/highlightjs/highlight.js/tree/main/src/styles)
to get the correct name for the style you want in step 3

Step 5: replace `<style-name>` in the code snippet in step 2 with the style
name found in the official GitHub repo, save, and enjoy the result

## Recommendation

The collection is huge, and I did not have time to look at all the styles.
However, here are the styles that I found most attractive.

- Light themes: `atom-one-light`
- Dark themes: `agate`, `atom-one-dark`, `base16/decaf`, `base16/danqing`, `base16/eighties`

## Demo

### SQL code

```sql
SELECT 
    C.CustomerID,
    C.FirstName,
    CA.AddressID,
    CA.AddressType,
    A.AddressID,
    CONCAT_WS(
        ', ', A.AddressLine1, A.AddressLine2,
        A.City, A.StateProvince, A.CountryRegion
    ) AS FullAdress
    
-- Join C and CA
FROM Customer AS C
LEFT JOIN CustomerAddress AS CA
ON C.CustomerID = CA.CustomerID

-- Join CA and A
LEFT JOIN Address as A
ON CA.AddressID = A.AddressID
```

### Python code

```python
class Point:
    """
    Represents a point in 2D space
    """

    def __init__(self, x: float = 0, y: float = 0) -> None:
        """
        Init the position of a new point
        :param x: x-coord
        :param y: y-coord
        """
        self.x = x
        self.y = y

    def move(self, dx: float, dy: float) -> None:
        """
        Moves a point
        :param dx: change in x-coord
        :param dy: change in y-coord
        :return:
        """
        self.x += dx
        self.y += dy


# Init two points
p1 = Point()
p2 = Point(1, 2)
print(p1.x, p1.y)
print(p2.x, p2.y)
```

### R code

```r
library(tidyverse)

models <- tibble::tribble(
    ~model_name,    ~ formula,
    "length-width", Sepal.Length ~ Petal.Width + Petal.Length,
    "interaction",  Sepal.Length ~ Petal.Width * Petal.Length
)

iris %>% 
    nest_by(Species) %>% 
    left_join(models, by = character()) %>% 
    rowwise(Species, model_name) %>% 
    mutate(model = list(lm(formula, data = data))) %>% 
    summarise(broom::glance(model))
```

### YAML

```yaml
- john:
    name: John Doe
    job: Web developer
    skills:
      - Python
      - Java
- jane:
    name: Jane Smith
    job: Data scientist
    skills:
      - Python
      - R
      - Scala
```