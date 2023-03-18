---
{"dg-publish":true,"permalink":"/parallel-coordinate/","title":"Parallel Coordinate","created":"2022-10-13T02:36:23","updated":"2022-12-11T21:44:09"}
---

> [!meta]-  
sup:: [[EDAV\|EDAV]]  
state:: done  
related:: [[EDAV - Multivariate Continuous Data\|EDAV - Multivariate Continuous Data]]

# Parallel Coordinate

Instead of making coordinates orthogonal, we can make them **parallel** to adapt more than 3 coordinates/variables. Just like line charts, parallel coordinate plots are for [[EDAV - Multivariate Continuous Data\|EDAV - Multivariate Continuous Data]].

## Slope Graph

When there are only two parallel coordinates, the graph is called a **slope graph**.

![](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221013024024.png)

To make the patterns in a slope graph more obvious, we can apply some data transformation

- Standardization: `(x - mean(x)) / sd(x)`
- Rescaling (to $[0,1]$): `scales::rescale()`

A drawback of these transformations is that we lose the actual units. A remedy is to label the units on each axis.

## More Variables

We can use `ggparcoord` in `GGally` to create parallel coordinate plots.

- `scale = "std"` (standardization) is the default scale
- `scale = "uniminmax"` is rescaling
- `scale = "globalminmax"` is the scale without transformation

Other methods to reveal the patterns:

- Reorder the variables
    - Making lines cross may be better than making them parallel
{ #o9j70v}

- Make lines transparent (change alpha)
- Interpolation
    - Instead of using straight lines, we can use splines or other interpolated curves
    - This helps separate lines sharing the same value of some variables
- Highlight a trend
    - Use colors to separate the trend and other lines

## Implementations

- `ggplot2::geom_line()`
    - Use [[tidyr\|tidyr]] to transform variable names to x-axis first
- `GGally::ggparcoord()` (static, ggplot2)
- `MASS:: parcoord()` (static, base)
- `parcoords::parcoords()` (interactive)
    - `devtools::install_github(“timelyportfolio/parcoords”)`
