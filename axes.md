# Axes

Given a data and Scales, the `d3.svg.axis()` Axes component creates a horizontal-axis or/and vertical-axis.

Axis function can be setup like

```javascript
var xaxis = d3.svg.axis()
```
You can provide sclae from previously defined xcale.
```javascript
xaxis.scale(xscale)
```
or
```javascript
var xaxis = d3.svg.axis()
          .scale(xscale)
```
also provide position like:
```javascript
xaxis.orient("bottom")
```
To generate the axis and into SVG, we must call the xaxis function:
```javascript
svg.append("g")
    .call(xaxis)
```

## Add Axis to Scatterplot

```javascript
//Define X axis
var xaxis = d3.svg.axis()
          .scale(xscale)
          .orient("bottom")
          .ticks(5)
//Define Y axis
var yaxis = d3.svg.axis()
          .scale(yscale)
          .orient("left")
          .ticks(5)
//Create X axis
svg.append("g")
  .attr("class", "axis")
  .attr("transform", "translate(0," + (height - padding) + ")")
  .call(xaxis)
//Create Y axis
svg.append("g")
  .attr("class", "axis")
  .attr("transform", "translate(" + padding + ",0)")
  .call(yaxis)

```
<iframe src="recipes/scatter-aob-saxis.html" sandbox="allow-same-origin allow-scripts" onload="this.style.height=this.contentDocument.documentElement.scrollHeight+2+'px';"></iframe>
