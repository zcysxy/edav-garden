---
{"dg-publish":true,"permalink":"/d3-bind-data/","title":"D3 Bind Data","created":"2022-12-01T20:45:08","updated":"2022-12-12T15:17:15"}
---


# D3 Bind Data

- `.data(data)` binds data to the selected elements
    - `.data` only accepts an **array** of values; `.data(2)` will not bind the data
    - if multiple elements are selected, ~~`data` can be an array of values~~; then values will automatically match the elements
    - `.data()` shows the data
- `.datum(datum)` binds a datum to all the selected elements
    - every selected element will get the same datum
    - the datum can be a scalar `2`
    - or it can be an array, then every selected element will get the same array

Binding data to elements using d3 will not make explicit changes to the element: the data will not show up in the [[DOM\|DOM]].

## Update, Enter, Exit

`.data()` will return an **update**, an **enter**, and an **exit** selection

- update selection contains the [[DOM\|DOM]] elements that match the data
    - update selection is stored in the `_groups` attribute of the return, which is the **default object** on which further actions will apply
- exit selection contains the [[DOM\|DOM]] elements that don't find data matches
    - exit selection is stored in the `_exit` attribute of the return; you can get it using method `.exit()`
        - then `_groups` of the return of `.exit()` will be the exit selection
    - matched element in the update selection will be *empty* in the exit selection
- enter selection contains non-existent "placeholder" elements for data that don't find object matches
    - enter selection is stored in the `_enter` attribute of the return; you can get it using method `.enter()`
        - then `_groups` of the return of `.enter()` will be the exit selection
    - matched element in the update selection will be *empty* in the enter selection
    - you can add *real* elements to the placeholder elements by `selection.enter().append()`

![|500](https://raw.githubusercontent.com/zcysxy/Figurebed/master/img/20221122164308.png)

> [!ex] Creating Elements Using Data
> Suppose we have an empty svg element and an array of data. We want to create three rectangles inside of the svg with the data.
>
> ```js
> const specialdata = [75, 150, 200];
> 
> d3.select("svg")
>   .selectAll("rect")
>   .data(specialdata)
>   .enter() // placeholder elements
>   .append("rect") // change/append placeholder elements with rectangles
>     .attr("x", d => d)
>     .attr("y", d => d)
>     .attr("width", "50")
>     .attr("height", "30")
>     .attr("fill", "pink");
> ```
>

> [!ex] Create a [[Bar Chart\|Bar Chart]]
>
> ```js
> let bardata = [300, 100, 150, 225, 75, 275];
> svg = d3.select("body")
>   .append("svg")
>     .attr("width", "700")
>     .attr("height", "400");
>     
> let bars = svg.selectAll("rect")
>   .data(bardata);
> 
> bars.enter()
>   .append("rect")
>     .attr("x", 0)
>     .attr("y",  (d, i) => i * 25 + 10)
>     .attr("width", d => d)
>     .attr("height", "20")
>     .attr("fill", "pink");
> ```
>

## Merge

The above examples manipulate the update, enter,  and exit selection respectively.
To do some manipulations on the broader selection after some manipulations on some selection, we can use the `.merge(other_selection)` function.

For example:

```js
const newdata = [123, 52, 232, 90, 34, 12, 189, 110];
const svg = d3.select("svg");
const circ = svg.selectAll("circle")
  .data(newdata);
  
circ.enter()  // 2 placeholders
  .append("circle")  // placeholders -> circles
     .attr("cx", "100")  // acts on enter selection only
     .attr("cy", (d, i) => (i - 5) * 50)
     .attr("r", "20")
     .attr("fill", "red")
  .merge(circ) // merge circ(update) into circ.enter
     .transition()
     .duration(2000)
     .attr("cx", "200");
```

Combine with a function:

```js
function changedata(data) {
  const bars = d3.select("svg#gup") 
    .selectAll("rect")
    .data(data);    // bars is the update selection
    
  bars.enter()
    .append("rect")
      .attr("x", "30")  // until merge, acts on
      .attr("y", (d, i) => i * 50) // enter selection only
      .attr("height", "35")  
      .attr("fill", "lightgreen")
    .merge(bars) // merge in the update selection
      .attr("width", d => d); // acts on all bars
      
  bars.exit()
    .remove();
}
```

The above function works no matter if `bars.enter()` or `bars.exit()` is empty.

## Groups

We can manually create groups by creating a parent element `<g>` for that group. For example:

```js
const svg = d3.select("svg");
const specialdata = [100, 250, 300];

const bars = 
  d3.select("svg")
    .append("g") // group parent element
      .attr("id", "rects")
    .selectAll("rect") // rects in the group g
    .data(specialdata)
    .enter()
    .append("rect")
      .attr("x", d => d)
      .attr("y", d => d)
      .attr("width", "50")
      .attr("height", "30")
      .attr("fill", "red");
```
