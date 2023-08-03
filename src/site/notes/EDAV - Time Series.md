---
{"title":"EDAV - Time Series","alias":null,"type":"note","created":"2022-11-01T16:53:01","modified":"2022-11-03T15:56:36","dg-publish":true,"sup":["edav"],"state":"done","permalink":"/edav-time-series/","dgPassFrontmatter":true,"updated":"2022-11-03T15:56:36"}
---


# Time Series

A time series is a sequence of data points, typically consisting of successive measurements made over a time interval. Visualizing time series data helps extract meaningful statistics and other characteristics of the data.

- When presenting time series data, use **lines** with time on the x-axis
- Use `Date` and `Date-Time` [[R Type\|R classes]] for time series

## Long-Term Trend

Time series graphs are good for exploring **overall long-term trends (secular)**.
Time series are essentially discrete data and have **short-term noise**. We can add a **loess smoother** to fit the data.

![](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221101170338.png)

In the above example, the blue curve is a global non-parametric smoother, while the red segments are linear smoothers constrained to specific time windows (groups). We can see that the smoothers eliminate the short-term noise (e.g. intra-weekly oscillations) and present the long-term trend.

Add a smoother using [[ggplot2\|ggplot2]]: `geom_smooth(method = "loess", span = .75, se = FALSE)`

- <span class="alt-check alt-check-tip">Choose the right parameters for smoothers to avoid [[Overfitting and Underfitting\|Overfitting and Underfitting]]. Small `span` tends to overfit; while large `span` tends to underfit.
{ #4j85jk}
</span>

> [!rmk] Rolling Average vs Smoother
> A rolling average and a smoother are alike, but they are not the same thing. A rolling average is fitting a **constant** instead of a line. Therefore, there are more *jumps* in a rolling average. Rolling averages only aggregate the previous information and do not capture future information.
>
>
> ![](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221103152814.png)

### Remove Cyclical Trends

In addition to smoothers, there are some other methods to eliminate the noise of short-term cyclical trends. The key idea is to extract a certain point in the cycle, and show the trend of this point among all cycles. For example, when there is a weekly cyclical trend, we can focus on the trend of Monday data. To achieve this, we can

- Highlight/label Monday data points
- Facet by weekdays
- Use special functions like `monthplot`

### Abnormalities

Abnormalities and outliers may violate the trend. To find the abnormalities, we can

- Use another feature/variable, which may be the cause of abnormalities, to label the data
- Highlight the abnormality

### Compare Multiple Lines

When using raw data to plot a multi-line plot, some lines will dominate others. To only compare the trends instead of values, we can scale the data using
$$
y_i' = 100 \cdot \frac{y_i}{y_{1}}.
$$

## Gaps

Line plots do not show the frequency of the data, and may hide **gaps**. We can add additional points to show the frequency.

![](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221103155133.png)

To explicitly show the gap, we can set missing values to NA (do not remove them).
Another option is to use facets.
