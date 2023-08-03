---
{"title":"Scatterplot","alias":null,"type":"note","created":"2022-10-12T23:24:08","modified":"2022-12-11T20:14:21","dg-publish":true,"sup":["[[EDAV\\|EDAV]]"],"state":"done","related":["[[EDAV - Dependency Relationship\\|EDAV - Dependency Relationship]]"],"permalink":"/scatterplot/","dgPassFrontmatter":true,"updated":"2022-12-11T20:14:21"}
---


# Scatterplot

A scatter plot uses Cartesian coordinates to display values for typically **two variables** for a set of data. The data are displayed as a collection of points, each having the value of two variables determining the position.

The major role of scatterplots lies in **revealing associations** ([[EDAV - Dependency Relationship\|EDAV - Dependency Relationship]]) between variables, not just linear associations, but any kind of association.

## Features

- Causal relationships
    - correlation ≠ causation, but we still use the y-axis for what appears to be the dependent variable
- Associations
    - describe what you see
- Outliers
- Clusters
- Gaps
- Barriers (boundaries)
- Conditional relationships
    - different relationships for different intervals of x

## An Example

![ggplot2movies: rating vs. votes (y ~ x)](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221012233459.png)

We can observe that

- Boundaries
    - No films have high votes and low ratings
    - No films have high votes and an average rating close to the maximum possible
- For films with more than a few votes, the average rating increases w/ # of votes
- Outliers: some films appear to have lower-than-expected ratings
- Films with low votes may have any average rating (full range)
    - The only films with very high ratings are those with relatively few votes

## Overplotting

As we can see in the above example, scatterplots may **overplot**, making dots stacked together. There are some strategies for this problem

- Change the points in some way
    - open circles
    - alpha blending
        - `geom_point(alpha = .3, stroke = 0)`
    - smaller dots
        - Default value in `geom_point` is `size = 1.5`
            - <span class="alt-check alt-check-tip">We can use `ggplot2:::check_subclass("point", "Geom")$default_aes` to see the default values in [[ggplot2\|ggplot2]]</span>
        - Make `shape = "."`
- Don't plot all points
    - randomly sample data
        - `|> slice_sample(n = 1000)`
    - subset data
        - static: by percentiles
        - interactive: [[R Package - Plotly\|ggplotly(), plot_ly()]]
    - remove outliers
- Transform to log scale
    - `+ scale_x_log10()`
    - `+ scale_x_log10(breaks = c(1, 10, 100, 1000, 10000))`

## Smooth Scatterplot

A smooth scatterplot is a combination of a scatterplot, a [[Heatmap\|Heatmap]], and a [[Density Contour Plot\|Density Contour Plot]]. It plots the points and uses colors and shapes to show the magnitude of clusters. Use the [[R\|R]] built-in function `smoothScatter(x,y)` to create a smooth scatterplot.

![](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221013010542.png)
