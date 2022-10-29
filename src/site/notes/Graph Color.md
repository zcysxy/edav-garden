---
{"dg-publish":true,"permalink":"/graph-color/"}
---

> [!meta]-  
sup:: [[EDAV|EDAV]]  
state:: done  

# Graph Color

## Link Between Data And Color

Match data types to color palettes/schemes

- Sequential <svg width="20" height="20" style="vertical-align: -4px; border:2px solid black "><rect width="20" height="20" style="fill:#FFFFFF"/></svg><svg width="20" height="20" style="vertical-align: -4px; border:2px solid black "><rect width="20" height="20" style="fill:#C0C0C0"/></svg><svg width="20" height="20" style="vertical-align: -4px; border:2px solid black "><rect width="20" height="20" style="fill:#808080"/></svg><svg width="20" height="20" style="vertical-align: -4px; border:2px solid black "><rect width="20" height="20" style="fill:#000000"/></svg>
    - suitable for **ordinal** variables
    - easy to tell the level of a color
    - e.g. [[Heatmap|Heatmap]]
- Diverging <svg width="20" height="20" style="vertical-align: -4px; border:2px solid black "><rect width="20" height="20" style="fill:#FF0000"/></svg><svg width="20" height="20" style="vertical-align: -4px; border:2px solid black "><rect width="20" height="20" style="fill:#FF7F00"/></svg><svg width="20" height="20" style="vertical-align: -4px; border:2px solid black "><rect width="20" height="20" style="fill:#FFFF00"/></svg><svg width="20" height="20" style="vertical-align: -4px; border:2px solid black "><rect width="20" height="20" style="fill:#7FFF00"/></svg><svg width="20" height="20" style="vertical-align: -4px; border:2px solid black "><rect width="20" height="20" style="fill:#00FF00"/></svg>
    - suitable for [[EDAV - Categorical Data#Likert Data|Likert Data]]
    - able to divide colors into groups
- Qualitative <svg width="20" height="20" style="vertical-align: -4px; border:2px solid black "><rect width="20" height="20" style="fill:#FF0000"/></svg><svg width="20" height="20" style="vertical-align: -4px; border:2px solid black "><rect width="20" height="20" style="fill:#007FFF"/></svg><svg width="20" height="20" style="vertical-align: -4px; border:2px solid black "><rect width="20" height="20" style="fill:#00FF00"/></svg>
    - suitable for [[EDAV - Categorical Data|Categorical Data]]
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
    - [@] ![](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221027170006.png)

## With ggplot2

- Continuous data
    - scheme function: `+scale_color_viridis_c()` (`c` for continuous)
    - palette option: `+scale_color_distiller(palette = "PuBu")`
    - own sequential: `+scale_color_gradient(low="white", hight="red")`
    - own diverging: `+scale_color_gradient2(low="blue", mid="white", hight="red")`
- Discrete data
    - scheme function: `+scale_color_viridis_d()` (`d` for discrete)
    - own: `+scale_color_manual(values=c("red", "yellow", "#FFFFFF")`

## With Other Packages

```r
library(RColorBrewer)
colors <- brew.pal(4, "Reds") # get the color codes
barplot(1:4,  col = colors)
```

## Color Vision Deficiency

To make color vision deficiency (CVD) friendly praphs,

- Use palettes that have already been tested
    - [@] viridis, `scale_color_colorblind()` in ggthemes
- Use a color vision deficiency simulator
    - [@] Color Oracle
- Use high contrast
