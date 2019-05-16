---
layout: page
title: Markdown-based page example
subtitle: Subtitle goes here
bigimg: /img/pubg2.jpg
---

## Killers And Damage Dealt:
1. The average kill of a player is 0.9247835321393355

(/img/image_1.png)

## How about a link?

And of course some text, and maybe [a link to https://datasci.columbian.gwu.edu/](https://datasci.columbian.gwu.edu/)

## Or some code?

Some code might go here:

```
x <- 5 # Here's some R code
```

What if I just paste the HTML for a plotly plot?

We can do it with a line of markdown that looks like this (without the slashes - I haven't solved that problem just yet...):
```
\{\% include jupyter-basic_bar.html \%\}
```
{% include jupyter-basic_bar.html %}
