---
{"title":"Cleveland Dot Plot","alias":null,"type":"note","created":"2022-10-12T21:20:51","modified":"2022-10-12T21:34:35","dg-publish":true,"sup":["edav"],"state":"done","related":["edav-categorical-data"],"permalink":"/cleveland-dot-plot/","dgPassFrontmatter":true,"updated":"2022-10-12T21:34:35"}
---


# Cleveland Dot Plot

The Cleveland dot plot is an alternative to [[Bar Chart\|Bar Chart]], replacing a bar with a single dot.

- Cleveland dot plots need to be sorted in descending order just like [[Bar Chart\|Bar Chart]]s
    - Use `fct_reorder` in [[forcats\|forcats]]
- Use `geom_point` in [[ggplot2\|ggplot2]] to create a Cleveland dot plot
- When you have other variables other than the categorical variable, Cleveland dot plots can easily adopt multiple dots
    - Use `fct_reorder2` in [[forcats\|forcats]] to reorder dots based on one variable
- Facets, the reasonable cut, and other techniques for [[EDAV - Categorical Data\|EDAV - Categorical Data]] apply to Cleveland dot plots

![|500](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221012213125.png)
