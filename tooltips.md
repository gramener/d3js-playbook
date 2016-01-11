# Tooltips

The Tooltips are small HTML elements that accompany visual objects to present data values, and usally appears when the user moves the mouse pointer over an element.

Let's take our countries scatterplot and add tooltips

```javascript
// Define the div for the tooltip
var tip = d3.select("body").append("div")
    .attr("class", "tooltip")
    .style("opacity", 0)
// Add events to circles
circles.on("mouseover", function(d) {
  tip.style("opacity", 1)
     .html(d.country + "<br/> Gold: " + d.gold + "<br/> Silver: " + d.silver)
     .style("left", (d3.event.pageX-25) + "px")
     .style("top", (d3.event.pageY-75) + "px")
  })
  .on("mouseout", function(d) {
    tip.style("opacity", 0)
  })
```
<iframe src="recipes/tooltip-scatter.html" sandbox="allow-same-origin allow-scripts" onload="this.style.height=this.contentDocument.documentElement.scrollHeight+2+'px';"></iframe>

By the way, we need to style the tooltip.

```css
.tooltip {
  position: absolute;
  pointer-events: none;
  background: #000;
  color: #fff;
}
```
