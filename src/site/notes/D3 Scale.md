---
{"title":"D3 Scale","alias":null,"type":"note","created":"2022-12-01T00:27:42","modified":"2022-12-12T13:11:22","dg-publish":true,"sup":["[[D3\\|D3]]"],"state":"done","permalink":"/d3-scale/","dgPassFrontmatter":true,"updated":"2022-12-12T13:11:22"}
---


# D3 Scale

Cartesian coordinates are different from the coordinates in an [[SVG\|SVG]].
![](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221201003039.png)

So we need transformers to map Cartesian coordinates to [[SVG\|SVG]] coordinates; **scales** in [[D3\|D3]] are such transformers.

There are two functions in [[D3\|D3]] to create scales: one for [[EDAV - Categorical Data\|Categorical Data]]—`.scaleBand()`, and one for [[EDAV - Continuous Variable\|Continuous Data]]—`.scaleLinear()`.
Note that these functions are for creating your own scales rather than alternating the current scales.

## Ordinal Scales

To create an [[EDAV - Categorical Data#Ordinal vs Nominal\|ordinal]] scale:

```js
const ordScale = d3.scaleBand()
    .domain(["cold", "warm", "hotel"])
    .range([0,600])
```

`.scaleBand()` evenly divide the range for each category.
`ordScale.bandwidth()` returns the bandwidth of the result.
And `ordScale(category)` returns the **left boundary** of the category band.

`.domain()` also accepts indexes of categories.
In this case, to make the above snippet more flexible, we can use `.domain(d3.range(dataset.length))` instead of `.domain([0,1,2,3,4])`.

- <span class="alt-check alt-check-tip">Don't mix up `d3.range()`, which returns an [[JS Type - Array\|array]] of integers, and `.domain().range()`.
{ #vga7uq}
</span>

To have some padding between bands, use `.paddingInner([paddingPercent1,...])`; then the padding will be `.bandwidth() * paddingPercent1`.
It won't add padding before the first band or after the last band.

## Continuous Scale

To create a continuous scale:

```js
const yScale = d3.scaleLinear()
    .domain([-100,100])
    .range([0,500])
```

Then `yScale(-100) == 0`, `yScale(0) == 250`, `yScale(50) == 375`, `yScale(100) == 500`.

A more flexible pattern would be

```js
const yScale = d3.scaleLinear()
    .domain([0,d3.max(data)])
    .range([svgHeight,0])
```

Then to create a vertical bar, we can set

- `rect.attr('y', d => yScale(d))`
- `rect.attr('height', d => svgHeight - yScale(d))`

## An Example

```js
// Set the size of the svg
const w = 400;
const h = 300;

// Create the svg
const svg = d3.select("body")
.append("svg")
  .attr("width", w)
  .attr("height", h)

// Bar height
const bardata = [5, 6, 10, 3, 2, 12];

// Ordinal x scale
const xScale = d3.scaleBand()
  .domain(d3.range(bardata.length))
  .range([0, w])
  .paddingInner(.1);

// Continuous y scale
const yScale = d3.scaleLinear()
  .domain([0, d3.max(bardata)])
  .range([h, 0])

// Create bars
const bars = svg.selectAll("rect")
  .data(bardata);

bars.enter().append("rect")
  .attr("x", (d, i) => xScale(i))
  .attr("width", xScale.bandwidth())
  .attr("y", d => yScale(d))
  .attr("height", d => h - yScale(d))
  .attr("fill", "lightgreen");

// Add text
svg.selectAll("text")
  .data(bardata)
  .enter()
  .append("text")
  .attr("x", (d, i) => xScale(i) + .5*xScale.bandwidth())
  .attr("y", d => yScale(d) + 25)
  .text(d => d)
  .attr("fill", "blue")
  .attr("text-anchor", "middle");
```

The result:

![|500](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221201011728.png)
