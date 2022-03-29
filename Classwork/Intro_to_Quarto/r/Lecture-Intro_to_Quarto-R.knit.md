---
title: "Welcome to Quarto!"
author: "YOUR NAME HERE"
format: 
  html:
    code-fold: true
    code-line-numbers: true
    code-tools: true
editor: visual
---

## Quarto

Quarto enables you to weave together content and executable code into a finished document. To learn more about Quarto see <https://quarto.org>.

The advantage of Quarto is that you can intersperse your text with your code and output with your ordinary text. This makes it easier to create nicely formatted reports, showing both the statistical analysis and the written discussion.

When you click the **Render** button a document will be generated that includes both content as well as the output of any embedded code chunks within the document:

::: {.cell}

```{.r .cell-code}
1 + 1
```

::: {.cell-output-stdout}
```
[1] 2
```
:::
:::


## Code Chunks

The "grey areas" above are called *code chunks*. This means that Quarto understands anything you write inside them to be code that should be executed by the computer.

Notice that this does not calculate anything:

100\*35

but this does:

::: {.cell}

```{.r .cell-code}
100*35
```

::: {.cell-output-stdout}
```
[1] 3500
```
:::
:::


What about this?

::: {.cell}

```{.r .cell-code}
# 100*35
```
:::


## Libraries

R and python are both *open-source* languages, meaning that they rely on "add-on" code, or **packages**, to add to the functionality of the language.

Many packages have been pre-installed for you. These include:

`tidyverse` for data manipulation and visualization

`tidymodels` for statistical learning

`here` and `janitor`, two helpful little packages we will use



Even though packages have been **installed** already, you still need to **declare your dependencies** at the start of every Quarto notebook:

::: {.cell}

```{.r .cell-code}
library(tidyverse)
```

::: {.cell-output-stderr}
```
-- Attaching packages --------------------------------------- tidyverse 1.3.1 --
```
:::

::: {.cell-output-stderr}
```
v ggplot2 3.3.5     v purrr   0.3.4
v tibble  3.1.6     v dplyr   1.0.8
v tidyr   1.2.0     v stringr 1.4.0
v readr   2.0.1     v forcats 0.5.1
```
:::

::: {.cell-output-stderr}
```
Warning: package 'tibble' was built under R version 4.1.3
```
:::

::: {.cell-output-stderr}
```
Warning: package 'tidyr' was built under R version 4.1.3
```
:::

::: {.cell-output-stderr}
```
Warning: package 'readr' was built under R version 4.1.1
```
:::

::: {.cell-output-stderr}
```
Warning: package 'dplyr' was built under R version 4.1.3
```
:::

::: {.cell-output-stderr}
```
-- Conflicts ------------------------------------------ tidyverse_conflicts() --
x dplyr::filter() masks stats::filter()
x dplyr::lag()    masks stats::lag()
```
:::

```{.r .cell-code}
library(tidymodels)
```

::: {.cell-output-stderr}
```
Registered S3 method overwritten by 'tune':
  method                   from   
  required_pkgs.model_spec parsnip
```
:::

::: {.cell-output-stderr}
```
-- Attaching packages -------------------------------------- tidymodels 0.1.3 --
```
:::

::: {.cell-output-stderr}
```
v broom        0.7.9      v rsample      0.1.0 
v dials        0.0.9      v tune         0.1.6 
v infer        0.5.4      v workflows    0.2.3 
v modeldata    0.1.1      v workflowsets 0.1.0 
v parsnip      0.1.7      v yardstick    0.0.8 
v recipes      0.1.16     
```
:::

::: {.cell-output-stderr}
```
-- Conflicts ----------------------------------------- tidymodels_conflicts() --
x scales::discard() masks purrr::discard()
x dplyr::filter()   masks stats::filter()
x recipes::fixed()  masks stringr::fixed()
x dplyr::lag()      masks stats::lag()
x yardstick::spec() masks readr::spec()
x recipes::step()   masks stats::step()
* Use tidymodels_prefer() to resolve common conflicts.
```
:::

```{.r .cell-code}
library(here)
```

::: {.cell-output-stderr}
```
here() starts at C:/Users/kelly/Dropbox/Teaching/STAT-434/Materials-qmd/01-Intro-Linear_Models
```
:::

```{.r .cell-code}
library(janitor)
```

::: {.cell-output-stderr}
```

Attaching package: 'janitor'
```
:::

::: {.cell-output-stderr}
```
The following objects are masked from 'package:stats':

    chisq.test, fisher.test
```
:::
:::




Now that we have loaded our packages, we can make some nice visuals:

::: {.cell}
::: {.cell-output-stderr}
```
`geom_smooth()` using formula 'y ~ x'
```
:::

::: {.cell-output-display}
![Figure 1. A beautiful plot.](Lecture-Intro_to_Quarto-R_files/figure-html/plot-r-1.png){width=672}
:::
:::


Note that the `echo: false` parameter was added to the code chunk to prevent printing of the code that generated the plot. We also used the `fig-cap` option to give a nice caption. There are many more of these "chunk options" that can control the behavior of your output!

## Saving, Previewing, Rendering

You do **not** have to render the Quarto file to save it. You can save your `.qmd` file in the ordinary ways: File \> Save, or Control + S, or clicking the disk icon.

To preview the file, and see changes in realtime, choose the "Settings" wheel and pick "Preview in Viewer Pane".

When you render the file, you are creating a "final" version. Here is what happens:

1.  The text is formatted nicely.

2.  The code chunks are all run, in order, from scratch.

3.  A `.html` file is automatically created with the finished product.

This means the order of your code chunks is very important! You might run code in a different order when you are interacting with your notebook directly, but this won't help you when it comes to knitting.

::: {.cell}

```{.r .cell-code}
mean(a)
```

::: {.cell-output-error}
```
Error in mean(a): object 'a' not found
```
:::

```{.r .cell-code}
a <- 1:5
```
:::



## R and python

Quarto works exactly the same whether you use R and python - but you can't use both at the same time.

The only difference is in the top section of the document, called the **YAML**. Can you spot the one line that turns an R-based `.qmd` document (the default) into a python-based one?
