---
{"title":"D3 Interactivity","alias":null,"type":"note","created":"2022-12-01T21:43:56","modified":"2022-12-02T10:54:18","dg-publish":true,"sup":["[[D3\\|D3]]"],"state":"done","permalink":"/d3-interactivity/","dgPassFrontmatter":true,"updated":"2022-12-02T10:54:18"}
---


# D3 Interactivity

Interaction contains two parts

- What do users do?
    - event listener
    - information needed
- What will happen?

This note consists of many examples.

## Do Something to the Event Element

- `.on(event, function)` passes `event` and the selection as `this`/`event.currentTarget` to `function` when `event` is fired

```js
// A function to turn the fill color to yellow:
function goYellow() {d3.select(this).attr("fill", "yellow")};

d3.select("svg").select("circle").on("mouseover", goYellow);
// This in goYellow() in this call will be "circle"

// Use an anonymous function
d3.select("svg").select("line").on("click", function()
    {d3.select(this).attr("stroke-width", "10");});

// Pass the event
d3.select("svg").on("click", function(event)
    {d3.select("text").text(`(${d3.pointer(event)})`)});
```

## Do Something Unrelated to the Event Element

```js
d3.select("svg")
  .on("click", function () { // a function unrelated to the event
    d3.select("svg")
      .append("text")
        .attr("x", "100")
        .attr("y", "40")
        .text("Hello World");
  });
```

##  Change an Attribute of the Event Element

```js
d3.select("line")
  .on("click",function() {
    d3.select(this).attr("stroke-width","10");
  });
```

##  Get the Value of an Attribute of the Event Element

Use `event.currentTarget` to get the event selection.

```js
d3.select("circle")
  .on("click",function(event) {
    const rad = d3.select(event.currentTarget).attr("r");
    d3.select("text")
      .text(`The radius is ${rad} pixels.`);
  });
```

- <span class="alt-check alt-check-tip">`.select(this)` can be used instead of `.select(event.currentTarget)`. In the context of event handlers, `this` is the element that received the event, a.k.a. what you clicked on if it's a click event.</span>

##  Do Something with the Data

```js
d3.select("circle")
  .data([{s:"red",sw:"15"}])
  .on("click",function(event, d) {    
      d3.select(event.currentTarget)
        .attr("stroke", d.s) // get the data
        .attr("stroke-width", d.sw);
  });
```

- <span class="alt-check alt-check-rmk">Note that starting with D3 v6, the data is the 2nd parameter to be passed: `function(event, d)`.
{ #7c3n0k}
</span>
- <span class="alt-check alt-check-rmk">In addition, note that you do not need to pass `d` again when accessing the data: we use `d.s` not `d => d.s`**.</span>

##  Get the Location of the Event

Use `.pointer(event)` or `d3.mouse(this)` (D3 v5) to get the event/cursor location.

```js
d3.select("svg")
  .on("click",function(event) {
    d3.select("text")
      .text(`(${d3.pointer(event).map(Math.round)})`)
  });
```

## Do Something with the Value of a Radio Button

A radio button with value: `<input type="radio" value="red">`. The value can be directly get using `this.value`.

```js
d3.selectAll("input") // button
  .on("click", function(event) {
    const favcolor = event.currentTarget.value;
    d3.select("p#color").style("color", favcolor);
    });
```
