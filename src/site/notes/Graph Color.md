---
{"dg-publish":true,"permalink":"/graph-color/","dgHomeLink":true,"dgPassFrontmatter":false,"dgShowBacklinks":true,"dgShowLocalGraph":true,"dgShowInlineTitle":true}
---

> [!meta]-  
sup:: [[EDAV|EDAV]]  
state:: done  

# Graph Color

## Link Between Data And Color

Match data types to color palettes/schemes

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
