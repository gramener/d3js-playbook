# Event Listeners

Event Listeners listen for specific events being triggered on specific DOM elements.

Remember, we did something like?

```javascript
d3.select("p")
  .on("click", function() {
  // Do something on click
  // Remember, we drew random barcharts?
})
```
We just *binded* an Event Listener to the *p* element.
This piece of code listens for any *click event* triggered when the user clicks on <p> element.

Events can "click", "mouseover", or "submit" or any [DOM event type](https://developer.mozilla.org/en-US/docs/Web/Events#Standard_events) supported by your browser

Let's take our age-old barchart

```javascript
var data = [120, 140, 100, 130, 150, 130, 190, 150, 190, 110,
            110, 140, 120, 100, 170, 120, 120, 160, 120, 180]
var chart = d3.select('svg')

var rects = chart.selectAll('rect')
  .data(data).enter()
  .append('rect')
  .attr('x', 0)
  .attr('y', function(d,i) {return i * 15})
  .attr('width', function(d) {return d})
  .attr('height', 14)

var labels = chart.selectAll("text")
  .data(data)
  .enter()
  .append("text")
  .text(function(d) {return d})
  .attr("y", function(d,i) {return i*15 + 10})
  .attr("x", function(d) {return d - 20})
  .attr("font-family", "sans-serif")
  .attr("font-size", "10px")
  .attr("fill", "white")
```
<iframe src="recipes/events.html" sandbox="allow-same-origin allow-scripts" onload="this.style.height=this.contentDocument.documentElement.scrollHeight+2+'px';"></iframe>

# Add click event
to rectangles print the datum under it and change the color to green-ish

```javascript
rects.on("click", function(d) {
  console.log(d)
  d3.select(this)
    .attr("fill" , "rgb(0,"+d+",0)")
})
```
<iframe src="recipes/events-click.html" sandbox="allow-same-origin allow-scripts" onload="this.style.height=this.contentDocument.documentElement.scrollHeight+2+'px';"></iframe>

# Add hover event

```javascript
rects.on("mouseover", function(d) {
  d3.select(this)
    .attr("fill" , "rgb(0,"+d+",0)")
})
```
<iframe src="recipes/events-hover-incomplete.html" sandbox="allow-same-origin allow-scripts" onload="this.style.height=this.contentDocument.documentElement.scrollHeight+2+'px';"></iframe>

But, everything changes to green color, doesn't quite look like hover, so we need do the following.

# Add hover out
```javascript
rects.on("mouseover", function(d) {
  d3.select(this)
    .attr("fill" , "rgb(0,"+d+",0)")
})

rects.on("mouseout", function(d) {
  d3.select(this)
    .attr("fill" , "black")
})
```
<iframe src="recipes/events-hover-complete.html" sandbox="allow-same-origin allow-scripts" onload="this.style.height=this.contentDocument.documentElement.scrollHeight+2+'px';"></iframe>

# Add transition
To make it, look like we are playing colorful music!

```javascript
rects.on("mouseover", function(d) {
  d3.select(this)
    .attr("fill" , "rgb(0,"+d+",0)")
})

rects.on("mouseout", function(d) {
  d3.select(this)
    .transition()
    .duration(1200)
    .attr("fill", "black")
})
```
<iframe src="recipes/events-hover-transition.html" sandbox="allow-same-origin allow-scripts" onload="this.style.height=this.contentDocument.documentElement.scrollHeight+2+'px';"></iframe>
