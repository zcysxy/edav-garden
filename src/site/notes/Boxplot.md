---
{"dg-publish":true,"permalink":"/boxplot/","dgHomeLink":true,"dgPassFrontmatter":false,"dgShowBacklinks":true,"dgShowLocalGraph":true,"dgShowInlineTitle":true}
---

> [!meta]-
sup:: [[EDAV|EDAV]]  
state:: done  

# Boxplot

Boxplots display individual outliers and robust statistics for the data, useful for identifying outliers and for **comparisons of distributions** across subgroups.

- Boxplots follow the 5-data summary
    - min, first quartile/ lower hinge, median, third quartile/ upper hinge, max
        - [ ] [[!tocheck|!tocheck]] Sometimes quartiles are different than hinges
- Area != number of data points; each area contains the same number of points
    - Area represents the **density**
- Outliers: data outside the **fences**
    - fences: upper-hinge + 1.5 x **H-spread**, lower-hinge - 1.5 x H-spread
    - H-spread/ interquartile/ forth spread: upper-hinge - lower-hinge
- A multiple-class boxplot should be **re-ordered by the median**

## Elements

- Box width
    - A disadvantage of boxplots is that they don't convey information on how big the different groups are
    - Set `varwidth = TRUE` in [[ggplot2|ggplot2]], the width of boxes will be proportional to $\sqrt{n}$
- Extreme outliers
    - We can define **outer fences** to be over 3 times the box length away from the box; then outliers outside outer fences are extreme outliers
