---
{"dg-publish":true,"permalink":"/d3-margin/","title":"D3 Margin","created":"2022-12-01T01:22:50","updated":"2022-12-01T20:53:33"}
---

> [!meta]-  
sup:: [[D3\|D3]]  
state:: done

# D3 Margin

To create margins for a plot, we need to *manually* set the inner height and width, and then translate the graph.

```js
// Margin Convention
const w = 500;
const h = 400;
const margin = {top: 25, right: 0, bottom: 25, left: 25};
const innerWidth = w - margin.left - margin.right;
const innerHeight = h - margin.top - margin.bottom;

// Add a canvas
const svg = d3.select("svg");
svg.append("rect")
   .attr("x", 0)
   .attr("y", 0)
   .attr("width", w)
   .attr("height", h)
   .attr("fill", "lightblue");

// Translate the content group
const bars = svg.append("g")
    .attr("transform",
         `translate (${margin.left},
                     ${margin.top})`)
    .selectAll("rect")
    .data(bardata);
```

Note that here we use [[JS Types - String#^literal\|ES6 template literals]].
