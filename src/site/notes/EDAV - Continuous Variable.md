---
{"dg-publish":true,"permalink":"/edav-continuous-variable/","dgHomeLink":true,"dgPassFrontmatter":false,"dgShowBacklinks":true,"dgShowLocalGraph":true}
---

> [!meta]-  
sup:: [[EDAV|EDAV]]  
state:: [[%wip|%wip]]  

# Continuous Variable

A **continuous variable** can in theory take any value over its range, as opposed to a **discrete variable**.

- [~] The real world is discrete: in practice data for continuous variables are generally **rounded** to some level of measurement accuracy.

## Features of Continuous Variables

- **Asymmetry**
    - the distribution may not be symmetric like [[Normal Distribution|Normal Distribution]]
    - the distribution may be skewed to the left or right
    - [@] distributions of income
- **Outliers**
    - there may be data far from the rest of the data
- **Multimodality**
    - the distribution may have more than one peak
- **Gaps**
    - There may be ranges of values within the data where no cases are recorded
- **Heaping**
    - some values may occur unexpectedly often
- **Rounding**
    - Only certain *round* values (like integers) are found
- **Errors/Impossibilities**

Different graphs emphasize different features.

## Graphs

- [[Histogram|Histogram]]
    - asymmetry
    - multimodality
    - gaps
    - heaping
    - rounding
- [[Boxplot|Boxplot]]
    - outliers
    - statistics
    - ❌ multimodality
- [[Density Curve|Density Curve]]
    - asymmetry
    - multimodality
    - ❌ gaps
    - ❌ heaping
- [[Ridgeline|Ridgeline]]
- [[Bar Chart|Bar Chart]]
    - gaps, heaping
- [[Dotplot|Dotplot]]
    - gaps


<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">

<div class="markdown-embed-title">



</div>


> [!meta]-
sup:: [[EDAV|EDAV]]  
state:: done  

# Heatmap

How does a heatmap work:

![Square heatmap of bin counts (binwidth = 5)](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20220922170714.png)

Heatmaps can be seen as two-dimensional [[Histogram|Histogram]]s. Therefore, [[Histogram#^e0e0f4|bin width]] is also an important element for heatmaps.

In [[ggplot2|ggplot2]], use `geom_bin2d()` to create a heatmap.

## Hex Heatmap

Rather than using squares, hex heatmaps use hexagons. Hexagons are more compact, provide more accurate information, and make more natural transitions. In [[ggplot2|ggplot2]], use `geom_hex`

![](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221013000420.png)

## Unfixed Shapes

When using unfixed shapes, we can think of heatmaps as colored [[Density Contour Plot|Density Contour Plot]]s. This kind of heatmaps is widely used for geographic patterns and thermal patterns.

![|500](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221013164229.png)

## Changing Colors

Colors in heatmaps show the magnitudes of the phenomenon (cluster). An example to change the color: `scale_fill_continuous(direction = 1, low = "grey", high = "purple")`

## Three Variables

The color can not only represent the magnitude of the cluster, but it can also represent a **third** variable. By doing this, heatmaps are no longer restricted to [[EDAV - Continuous Variable|Continuous Variable]]s, but can also for [[EDAV - Categorical Data|categorical]].

For three variables, we cannot use `geom_bin2d` anymore. Some choices in [[ggplot2|ggplot2]] are

- `geom_tile`: plots a dot as a tile, with specified width and height
    - use `color = white` to add white borders to the tiles
- `geom_rect`: plots a dot as a rectangle, with specified `xmin,xmax,ymin,ymax`
    - Rectangles can be squares with `coord_fixed()`
- `geom_raster`: same as `geom_tile` w/ uniform width and height, and is faster

The above functions only plot the tiles without colors. Use `aes(fill = z)` to fill the colors according to variable `z`.


</div></div>
