---
{"dg-publish":true,"permalink":"/edav-continuous-variable/","title":"EDAV - Continuous Variable","created":"2022-09-26T00:35:53","updated":"2022-12-11T01:07:55"}
---

> [!meta]-  
sup:: [[EDAV\|EDAV]]  
state:: done

# Continuous Variable

A **continuous variable** can in theory take any value over its range, as opposed to a **discrete variable**.

- [~] The real world is discrete: in practice data for continuous variables are generally **rounded** to some level of measurement accuracy.

## Features of Continuous Variables

- **Asymmetry**
    - the distribution may not be symmetric like [[Normal Distribution\|Normal Distribution]]
    - the distribution may be skewed to the left or right
        - A distribution is called skewed **left/negative** if, as in the distribution graph, the left tail (smaller values) is much longer than the right tail (larger values)
        - A distribution is called skewed **right/positive** if, as in the distribution graph, the right tail (larger values) is much longer than the left tail (smaller values)
        - ![](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221210173449.png)
    - [@] distributions of income
- **Outliers**
    - there may be data far from the rest of the data
- **Multimodality**
    - the distribution may have more than one peak
    - the ==mode== is the value that appears most often in a set of data values
        - For a discrete [[Random Variable\|Random Variable]], the mode is $\argmax_{k}P(X=k)$
        - For a continuous [[Random Variable\|Random Variable]], the mode is the local maxima of the [[Probability Density Function\|PDF]]
- **Gaps**
    - There may be ranges of values within the data where no cases are recorded
- **Heaping**
    - some values may occur unexpectedly often
- **Rounding**
    - Only certain *round* values (like integers) are found
- **Errors/Impossibilities**

Different graphs emphasize different features.

## Graphs

- [[Histogram\|Histogram]]
    - asymmetry
    - multimodality
    - gaps
    - heaping
    - rounding
- [[Boxplot\|Boxplot]]
    - outliers
    - statistics
    - ❌ multimodality
- [[Density Curve\|Density Curve]]
    - distribution
    - asymmetry
    - multimodality
    - ❌ gaps
    - ❌ heaping
- [[Ridgeline\|Ridgeline]]
- [[Bar Chart\|Bar Chart]]
    - gaps, heaping
    - [~] treating discrete values as [[EDAV - Categorical Data\|Categorical Data]]
- [[Cleveland Dot Plot\|Cleveland Dot Plot]]
    - gaps
    - [-] heaping
- [[Q-Q Plot\|Q-Q Plot]]
    - distribution
    - asymmetry
    - multimodality

## Combine Continuous Variables and Categorical Variables


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/edav-categorical-data/#combine-continuous-variables-and-categorical-variables" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



## Combine Continuous Variables and Categorical Variables

When combining [[EDAV - Continuous Variable\|Continuous Variable]]s and [[EDAV - Categorical Data\|Categorical Variable]]s, we should consider

- mapping options:
    - Continuous: x-axis, y-axis, color (not so great), size (not so great)
    - Categorical: color, facets (rows, columns), shape (maybe)
- Add one variable at a time
- Create more graphs if suitable options run out
- Switch options to test


</div></div>

