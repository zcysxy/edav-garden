---
{"dg-publish":true,"permalink":"/histogram/","dgHomeLink":true,"dgPassFrontmatter":false,"dgShowBacklinks":true,"dgShowLocalGraph":true,"dgShowInlineTitle":true}
---

> [!meta]-
sup:: [[EDAV|EDAV]]  
state:: done  

# Histogram

A histogram is a graph grouping data into intervals, and drawing a bar for each interval, shows the empirical distribution

- [~] It's a *discrete* distribution, where events are intervals but not values

For example, the **frequency histogram** of data `50, 51, 53, 55, 56, 60, 65, 65, 68` with **`binwidth = 5`**.

![](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20220908164904.png)

## Elements

- Boundaries
    - Specify the boundaries to eliminate the confusion
    - You can choose boundaries to be NON-round numbers, to make sure no data lie on the boundaries
- Bin width ^e0e0f4
    - Choose the right bin width to better present the data
        - thin width will provide more details, but may not be necessary and give gaps
            - thin bins are useful to look for **gaps** and **heaping**
        - wide width will wipe out much information
    - Changing the bin width can help discover the **rounding pattern**
    - **Uneven bin widths**
        - When using uneven bin widths, use a **density** histogram
            - ![](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20220926010135.png)

## Types

In a histogram, the x-axis is the [[EDAV - Continuous Variable|Continuous Variable]] to be inspected. And Different **y-scales** gives different types of histograms.

- Frequency histogram
- Density histogram
    - In a density histogram, the **area** of a bar equals to the **relative frequency**; thus the y-scale is the *density*: $\text{relative frequency} / \text{binwidth}$
    - ![](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20220908165957.png)
    - ![](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20220908170007.png)
    - In [[ggplot2|ggplot2]], use `y = ..density..` to specify this scale
    - It is also very useful to overlay a **density line** (`geom_density()`)
- Cumulative frequency histogram
    - is suitable when some frequencies are small to present
    - ![](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20220908170058.png)
