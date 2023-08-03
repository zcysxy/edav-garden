---
{"type":"note","created":"2022-10-06T16:42:45","modified":"2022-12-11T22:35:07","dg-publish":true,"sup":[{}],"state":"done","permalink":"/mosaic-plot/","dgPassFrontmatter":true,"updated":"2022-12-11T22:35:07"}
---


# Mosaic Plot

A mosaic plot is a filled rectangular plot (no white space) with consistent numbers of rows and columns, in which the area of each small rectangle is proportional to the frequency count for a unique combination of levels of the categorical variables displayed.

- Mosaic plots are like stacked [[Bar Chart\|Bar Chart]]s, except that the width and height of the bars are proportional to the amount of data.
- Mosaic plots are not **treemaps**, which are another type of filled rectangular plots representing **hierarchical data** (fill color does not necessarily represent frequency count)
- Mosaic plots with only one horizontal cut (variable) are called ==spine plots==, where vertical cuts are called ==spines==
- Mosaic plots with the same bin width are relative frequency stacked [[Bar Chart\|Bar Chart]]s
    - All bars sum up to 100%, thus have the same height

![|400](https://upload.wikimedia.org/wikipedia/commons/8/84/Mosaic-big.png)

![U.S. adults who closely follow local news|500](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221013150806.png)

You can not read the actual values in a mosaic plot, but you can inspect the **association**. As we can see from the above example, we can relatively confident in concluding that the older one is, the higher probability of them being a follower.
The *steeper* the *stairs*, the stronger the relationship.

## More Variables

Mosaic plots are powerful for presenting [[EDAV - Multivariate Categorical Data\|Multivariate Categorical Data]]. We can put multiple variables on the x-axis and y-axis. The most important problem is **cutting** the variables.

![](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221013185846.png)

As in the above example, we put variables

- `Infl` and `Type` on the x-axis
    - We first cut on `Type`, and in each `Type`, we cut on `Infl`
- `Cont` and `Sat` on the y-axis
    - We first cut on `Cont`, and in each `Cont`, we cut on `Sat`

## Mosaic Pairs Plot

Just like [[Scatterplot Matrix\|Scatterplot Matrix]], we can make mosaic plot matrix, with each element being a spine plot with two variables. Then for $n$ variables, we need an $n\times n$ matrix. A diagonal elements is a vertical proportion cut of one variable.

![](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221211221648.png)

## Best Practices

- The order of cuts
    - Split dependent variables last
- Direction of cuts
    - Split dependent variables horizontally
    - 3 vars: VVH
    - 4 vars: VVVH
    - 5 vars: VHVVH
- Color fill is set to a dependent variable
    - Use color to stress the relationship
        - <span class="alt-check alt-check-ex">![|100x100](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221013192907.png) vs. ![|100x100](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221013192932.png)</span>
- The most important level of the dependent variable is the closest to the x-axis and with the most noticeable shade

## Implementation

- `geom_mosaic` in [[ggplot2\|ggplot2]]
- `mosaic()` in package `vcd`
    - <span class="alt-check alt-check-ex">`mosaic(Music ~ Age, data = counts3, direction = c("v", "h"))`</span>
    - <span class="alt-check alt-check-ex">`mosaic(Music ~ Age + Favorite, data = counts3, direction = c("v", "v", "h"))`</span>
    - Here [[R Type - Formula\|R Type - Formula]] can be read as "on", especially for dependent variables
{ #hv0kpp}

    - There should be a `Freq` column in the date, which is a standard column in a dataframe
    - use `vcd::labelings` functions to
        - abbreviate labels using option `abbreviate_labs = c(FALSE, 3, 6)`
        - rotate labels using option `rot_labels = c(0,0,0,0)`
        - adjust variable names using option `set_varnames = c('name1', 'name2')`
    - use `vcd::spacings` functions to adjust the spacing between factor levels

## Simpson's Paradox

Simpson's paradox is a phenomenon in [[Probability Theory\|Probability Theory]] and [[Statistics\|Statistics]] in which a trend appears in several groups of data but disappears or reverses when the groups are combined.
An example of Simpson's paradox is [[A Plausible Treatment Test\|A Plausible Treatment Test]].
A visual example of Simpson's paradox:

![200x200](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221013222838.png) ==> ![200x200](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221013222903.png)

Mosaic plots can help eliminate Simpson's paradox:

![](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221013223143.png)
