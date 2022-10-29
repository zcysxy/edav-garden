---
{"dg-publish":true,"permalink":"/density-contour-plot/"}
---

> [!meta]-  
sup:: [[EDAV|EDAV]]  
state:: done  

# Density Contour Plot

Density contour lines are two-dimensional [[Density Curve|Density Curve]]s. So the relationship between density contour lines and [[Heatmap|Heatmap]]s is like that between [[Density Curve|Density Curve]]s and [[Histogram|Histogram]]s.

![](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221013004634.png)

Density contour plots use **kernel density estimates** to calculate the curves.

- The "number of bins" in a density contour plot is the number of lines
- When using facets, watch out for the boundaries
    - clustered points may be separated into two facets, causing wrong density estimates for two facets

## Implementation

- `kde2d` in package `MASS`

```r
library(GDAdata)
library(MASS)
f1 <- kde2d(SpeedSki$Year, SpeedSki$Speed, n = 100)
image(f1)
contour(f1, add = T)
```

- `geom_density_2d()`  and `geom_density_2d_filled()` in [[ggplot2|ggplot2]]

```r
library(GDAdata)
ggplot(SpeedSki, aes(Year, Speed)) +
    geom_density_2d() +
    geom_density_2d_filled(alpha = 0.7)
```

- Calculate using `kde2d`, plot with `geom_contour` in [[ggplot2|ggplot2]]

```r
ggplot(con2tr(f1, aes(x, y)) + geom_contour(aes(z = z))
```
