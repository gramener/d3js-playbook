# Scatter Plot

Two-dimensional data is commonly visualized using a scatter-plot. Where two dimensions are represented on two different axes, horizontal x and vertical y.

## Data

Array of arrays - contain one point for each primary array.

```javascript
var data = [
  [10, 20], [20, 100], [200, 50],
  [25, 80], [10, 200], [150, 75],
  [10, 70], [30, 150], [100, 15]
]

var svg = d3.select("body")
            .append("svg")
            .attr("width", 250)
            .attr("height", 250)

svg.selectAll("circle")
   .data(data).enter()
   .append("circle")
   .attr("cx", function(d) {return d[0]})
   .attr("cy", function(d) {return d[1]})
   .attr("r", 4)
```
<iframe src="recipes/scatter.html" sandbox="allow-same-origin allow-scripts" onload="this.style.height=this.contentDocument.documentElement.scrollHeight+2+'px';"></iframe>

## Size

```javascript
   .attr("r", function(d) {
     return Math.sqrt(d[0]*d[0]+d[1]*d[1])/20
   })

```
<iframe src="recipes/scatter-size.html" sandbox="allow-same-origin allow-scripts" onload="this.style.height=this.contentDocument.documentElement.scrollHeight+2+'px';"></iframe>

## Color

```javascript
   .attr("fill", function(d) {
     return "rgb("+d[0]+","+d[1]+",0)"
   })

```
<iframe src="recipes/scatter-color.html" sandbox="allow-same-origin allow-scripts" onload="this.style.height=this.contentDocument.documentElement.scrollHeight+2+'px';"></iframe>

## Labels

```javascript
// In addition to circles construction
svg.selectAll("text")
  .data(data).enter()
  .append("text")
  .attr("x", function(d) {return d[0]+4})
  .attr("y", function(d) {return d[1]+4})
  .text(function(d) {return d[0] + ", " + d[1]})
  .attr("font-size", "10px")

```
<iframe src="recipes/scatter-label.html" sandbox="allow-same-origin allow-scripts" onload="this.style.height=this.contentDocument.documentElement.scrollHeight+2+'px';"></iframe>

## Array of Objects

Let's make some readable data using array of objects

```javascript
var data = [
  {country:"USA", gold:10, silver:20},
  {country:"China", gold:20, silver:100},
  {country:"India", gold:200, silver:50},
  {country:"Russia", gold:25, silver:80},
  {country:"Germany", gold:10, silver:200},
  {country:"UK", gold:150, silver:75},
  {country:"France", gold:10, silver:70},
  {country:"UAE", gold:30, silver:150},
  {country:"Canada", gold:100, silver:15}
]

var svg = d3.select("body")
            .append("svg")
            .attr("width", 250)
            .attr("height", 250)

svg.selectAll("circle")
   .data(data).enter()
   .append("circle")
   .attr("cx", function(d) {return d.gold})
   .attr("cy", function(d) {return d.silver})
   .attr("r", function(d) {
     return Math.sqrt(d.gold*d.gold+d.silver*d.silver)/20
   })
   .attr("fill", function(d) {
     return "rgb("+d.gold+","+d.silver+",0)"
   })

svg.selectAll("text")
  .data(data).enter()
  .append("text")
  .attr("x", function(d) {return d.gold+10})
  .attr("y", function(d) {return d.silver+4})
  .text(function(d) {return d.country})
  .attr("font-size", "10px")
```

<iframe src="recipes/scatter-aob.html" sandbox="allow-same-origin allow-scripts" onload="this.style.height=this.contentDocument.documentElement.scrollHeight+2+'px';"></iframe>
