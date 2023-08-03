[object Promise]

# Scatterplot Matrix

If we want to show the relationships between $n \geq 2$ variables $\{ x_i \}_{i=1}^{n}$ using [[Scatterplot\|Scatterplot]]s, we need $\sum_{i=1}^{n}\sum_{j>i}^{n} 1 = n(n-1) /2$ scatterplots. If we plot $x _i \sim x_j$ and  $x_j \sim x _i$ as two different plots, then we have $n^{2} - n$ plots. Then adding labels, we have a scatterplot matrix.

![](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221013011906.png)

- <span class="alt-check alt-check-tip">When passing multiple variables to the [[R\|R]] built-in function `plot`, it will create a scatterplot matrix.</span>
- <span class="alt-check alt-check-rmk">While this is quite useful for personal exploration of a dataset, it is **not** recommended for presentation purposes. Something called the [Hermann grid illusion](https://en.wikipedia.org/wiki/Grid_illusion) makes this plot very difficult to examine.</span>

Other implementations

- `ggpairs()` in `GGally`
- `splom()` in `lattice`
