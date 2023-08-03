[object Promise]

# Graph Color

## Link Between Data And Color

Match data types to color palettes/schemes

- Sequential <svg width="20" height="20" style="vertical-align: -4px; border:2px solid black "><rect width="20" height="20" style="fill:#FFFFFF"/></svg><svg width="20" height="20" style="vertical-align: -4px; border:2px solid black "><rect width="20" height="20" style="fill:#C0C0C0"/></svg><svg width="20" height="20" style="vertical-align: -4px; border:2px solid black "><rect width="20" height="20" style="fill:#808080"/></svg><svg width="20" height="20" style="vertical-align: -4px; border:2px solid black "><rect width="20" height="20" style="fill:#000000"/></svg>
{ #1dc7c8}

    - suitable for **ordinal** variables
    - easy to tell the level of a color
    - e.g. [[Heatmap\|Heatmap]]
- Diverging <svg width="20" height="20" style="vertical-align: -4px; border:2px solid black "><rect width="20" height="20" style="fill:#FF0000"/></svg><svg width="20" height="20" style="vertical-align: -4px; border:2px solid black "><rect width="20" height="20" style="fill:#FF7F00"/></svg><svg width="20" height="20" style="vertical-align: -4px; border:2px solid black "><rect width="20" height="20" style="fill:#FFFF00"/></svg><svg width="20" height="20" style="vertical-align: -4px; border:2px solid black "><rect width="20" height="20" style="fill:#7FFF00"/></svg><svg width="20" height="20" style="vertical-align: -4px; border:2px solid black "><rect width="20" height="20" style="fill:#00FF00"/></svg>
    - suitable for [[EDAV - Categorical Data#Likert Data\|Likert Data]]
    - able to divide colors into groups
- Qualitative <svg width="20" height="20" style="vertical-align: -4px; border:2px solid black "><rect width="20" height="20" style="fill:#FF0000"/></svg><svg width="20" height="20" style="vertical-align: -4px; border:2px solid black "><rect width="20" height="20" style="fill:#007FFF"/></svg><svg width="20" height="20" style="vertical-align: -4px; border:2px solid black "><rect width="20" height="20" style="fill:#00FF00"/></svg>
    - suitable for [[EDAV - Categorical Data\|Categorical Data]]
    - There should not be some colors that stand out more than other colors
        - Unless you are stressing certain values

## Perceptually Uniform Color Spaces

We want to perceive the difference between data by observing colors.

![](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221027165208.png)

## Distinctions In Data

- The rate of color change should be consistent
    - This is also required by perceptually uniformness
    - [-] Color scheme `rainbow` is not perceptually uniform
- Large range
    - the color range should be large enough to help distinguish differences
- Sharp break at important thresholds
    - <span class="alt-check alt-check-ex">![](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221027170006.png)</span>

## With ggplot2

- Continuous data
    - scheme function: `+scale_color_viridis_c()` (`c` for continuous)
    - palette option: `+scale_color_distiller(palette = "PuBu")`
    - own sequential: `+scale_color_gradient(low="white", hight="red")`
    - own diverging: `+scale_color_gradient2(low="blue", mid="white", hight="red")`
- Discrete data
    - scheme function: `+scale_color_viridis_d()` (`d` for discrete)
    - palette option: `+scale_color_brewer(palette = "PuBu")`
    - own: `+scale_color_manual(values=c("red", "yellow", "#FFFFFF")`
- <span class="alt-check alt-check-rmk">The `color` in the above scales can be `fill` for scaling the `fill` variable</span>
- <span class="alt-check alt-check-rmk">continuous vs discrete: `c` vs `v`, `distiller` vs `brewer`, `gradient` vs `manual`
{ #v99m26}
</span>

## With Other Packages

```r
library(RColorBrewer)
colors <- brew.pal(4, "Reds") # get the color codes
barplot(1:4,  col = colors)
```

## Color Vision Deficiency

To make color vision deficiency (CVD) friendly graphs,

- Use palettes that have already been tested
    - <span class="alt-check alt-check-ex">viridis, `scale_color_colorblind()` in ggthemes</span>
- Use a color vision deficiency simulator
    - <span class="alt-check alt-check-ex">Color Oracle</span>
- Use high contrast

## General Tips

- Be consistent with colors
    - the color of the same object should be consistent among different graphs
    - manually set up the color if needed
- Legend order matches graph order
    - If your legend is on the right, it better matches the right ends of the graph
    - try label instead of legend
    - for some plots, like [[Bar Chart\|Bar Plot]], legends at the bottom may be better
- Sequential scheme for [[EDAV - Continuous Variable\|Continuous Data]]; qualitative scheme for [[EDAV - Categorical Data\|Categorical Data]]
- Do not use diverging scheme for non-likert data
- Colors should be a separate dimension
    - if a variable is already presented along the x-axis, there is no need to color the variable
