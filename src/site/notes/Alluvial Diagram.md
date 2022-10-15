---
{"dg-publish":true,"permalink":"/alluvial-diagram/","dgHomeLink":true,"dgPassFrontmatter":false,"dgShowBacklinks":true,"dgShowLocalGraph":true,"dgShowInlineTitle":true}
---

> [!meta]-  
sup:: [[EDAV|EDAV]]  
state:: done  

# Alluvial Diagram

Alluvial diagrams take inspiration from alluvial fans.
They use [[Parallel Coordinate|Parallel Coordinate]]s for [[EDAV - Multivariate Categorical Data|Multivariate Categorical Data]].
They show how data move from one category to some other categories.
Alluvial diagrams work well for data with *flow* in it. Observations with the same movement are drawn together to show the flow.
Some examples of data types that are suitable for alluvial diagrams are

- Hierarchical data
- Temporal data

![](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221013170436.png)

Other than axes, we can use colors for one variable to better visualize the patterns. The variable we choose to color should be our most interested one.

Different categories in axes are called ==strata==. Without alluviums, these strata form a [[Bar Chart|Bar Chart]].
The height of the strata and flows represent the size of the clusters.

## Implementation

We can use `geom_alluvium` in package `ggalluvial` to draw alluvial diagrams.

```r
library(ggalluvial)
ggplot(
    as.data.frame(UCBAdmissions),
    aes(y = Freq, axis1 = Gender, axis2 = Dept, axis3 = Admit)
) +
    geom_flow(aes(fill = Gender), width = 1/12) +
    geom_stratum(width = 1/12, fill = "grey80", color = "grey") +
    geom_label(
        stat = "stratum",
        aes(label = after_stat(stratum))
    ) +
    scale_x_discrete(expand = c(.05, .05)) +
    scale_fill_brewer(type = "qual", palette = "Set1") +
    ggtitle("UC Berkeley admissions and rejections") +
    theme_void()
```

An important feature of an alluvial diagram is the **consistent flow**, which means an observation is a continuous curve.
While we can use `geom_flow` to create similar diagrams, where flows may not be connected. Such diagrams are only useful if you only focus on the association between adjacent categorical variables.

![](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221013182109.png)

## Loads Form

- Able to present *ghost* data, which doesn't have all categorical variables
- Need not specify the axes
