---
{"title":"D3 Axes","alias":null,"type":"note","created":"2022-12-01T16:35:19","modified":"2022-12-01T20:13:33","dg-publish":true,"sup":[{}],"state":"done","permalink":"/d3-axes/","dgPassFrontmatter":true,"updated":"2022-12-01T20:13:33"}
---


# D3 Axes

To render axes in [[D3\|D3]], we need to first generate them, and then plot them.
There are four axis generators called axis components:

- `.axisTop()`
- `.axisBottom()`
- `.axisLeft()`
- `.axisRight()`

Axis components control the orientation of the axis, but not the location. All axes are rendered at the origin.

There are two ways to pass a scale to an axis:

- `d3.axisBottom().scale(xScale)`
- `d3.axisBottom(xScale)`

To plot the axis, **call** it on **a selection**, then some [[SVG\|SVG]] elements presenting the axis will be created as a child of that selection. Also, there are two ways:

- `d3.select("svg").append("g").call(xAxis)`
- `xAxis(d3.select("svg").append("g"))`

Since all axes are rendered at the origin, we need to translate them. For example:

```js
const yAxis = d3.axisLeft().scale(yScale);
const svg = d3.select("svg")

svg.append("g")
   .attr("class", "yAxis")
   .attr("transform",
     `translate(${margin.left}, ${margin.top})`)
   .call(yAxis);
```

## Ticks

To label the ticks, use labels when creating the [[D3 Scale\|D3 Scale]]. For example, for data

```js
const bardata = [{month: "Jan", value: 300},
                 {month: "Feb", value: 100},
                 {month: "Mar", value: 150},
                 {month: "Apr", value: 220},
                 {month: "May", value: 70 },
                 {month: "Jun", value: 270}]
```

we can create the x ordinal scale using `month`,

```js
const xScale = d3.scaleBand()
  .domain(bardata.map(d => d.month))
  .range([0, innerWidth])
  .paddingInner(.1);
```

and then create y continuous scale using `value`. Then the axes will automatically comply with the scale.

Or, we can add the tick values *explicitly*

```js
const yAxis = d3.axisLeft(xScale).tickValues([1, 2, 3, 5, 8, 13, 21]);
```
