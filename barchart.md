# Bar Chart

Now, if we were to manually create a bar chart in SVG. We would do something like,

```html
<svg>
  <rect x="0" y="0"  width="120" height="25"/>
  <rect x="0" y="30" width="140" height="25"/>
  <rect x="0" y="60" width="150" height="25"/>
  <rect x="0" y="90" width="180" height="25"/>
</svg>
```

<svg>
  <rect x="0" y="0"  width="120" height="25"/>
  <rect x="0" y="30" width="140" height="25"/>
  <rect x="0" y="60" width="150" height="25"/>
  <rect x="0" y="90" width="180" height="25"/>
</svg>

Let's use d3 to do the same

## Create barchart

```javascript
var data = [120, 140, 150, 180]  // define width is array
var chart = d3.select('svg')     // select svg
  .selectAll('rect')
  .data(data).enter()
  .append('rect')
  .attr('x', 0)
  .attr('y', function(d,i) {return i * 30})
  .attr('width', function(d) {return d})
  .attr('height', 25)
```
<iframe src="http://jsbin.com/wusivi/embed?js,output" style="border: 1px solid rgb(170, 170, 170); width: 100%; min-height: 300px; height: 30px;"></iframe>

## Add text

```javascript
// After creating basic barchart
d3.select('svg').selectAll("text")
  .data(data)
  .enter()
  .append("text")
  .text(function(d) {return d})
  .attr("y", function(d,i) {return i*30 + 20})
  .attr("x", function(d) {return d})
```
<iframe src="recipes/horizontal-bar-labels.html" sandbox="allow-same-origin allow-scripts" onload="this.style.height=this.contentDocument.documentElement.scrollHeight+2+'px';"></iframe>

Shall we make the chart look a bit pretty? By, just changing position, color, size of text!

```javascript
d3.select('svg').selectAll("text")
  .data(data)
  .enter()
  .append("text")
  .text(function(d) {return d})
  .attr("y", function(d,i) {return i*30 + 15})
  .attr("x", function(d) {return d - 20})
  .attr("font-family", "sans-serif")
  .attr("font-size", "10px")
  .attr("fill", "white")
```
<iframe src="recipes/horizontal-bar-labels-pretty.html" sandbox="allow-same-origin allow-scripts" onload="this.style.height=this.contentDocument.documentElement.scrollHeight+2+'px';"></iframe>
