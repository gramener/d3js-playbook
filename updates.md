# Updates

This was our original bar-chart.

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
<iframe src="recipes/updates-bar.html" sandbox="allow-same-origin allow-scripts" onload="this.style.height=this.contentDocument.documentElement.scrollHeight+2+'px';"></iframe>

## Update __data__

Now, on click of <p> tag let's update the barchart with random data.

```javascript
var data = [120, 140, 150, 180]
var chart = d3.select('svg').selectAll('rect')
  .data(data).enter()
  .append('rect')
  .attr('x', 0)
  .attr('y', function(d,i) {return i * 30})
  .attr('width', function(d) {return d})
  .attr('height', 25)

d3.select("p")
  .on("click", function() {  // Event listener - later about that!
    // create random data
    data = random(4)         // Custom function, we can write your own!
    // update rect widths with enw data
    d3.select('svg')
      .selectAll("rect")     // select rects to be updated
      .data(data)            // New data binded to rects
      .attr('width', function(d) {return d}) // visual attribute to be updated
  })
```
<iframe src="recipes/updates-bar-pclick.html" sandbox="allow-same-origin allow-scripts" onload="this.style.height=this.contentDocument.documentElement.scrollHeight+2+'px';"></iframe>

## Updating labels too

```javascript
d3.select("p")
  .on("click", function() {  // Event listener - later about that!
    // create random data
    data = random(4)         // Custom function, we can write your own!
    // update rect widths with enw data
    d3.select('svg')
      .selectAll("rect")     // select rects to be updated
      .data(data)            // New data binded to rects
      .attr('width', function(d) {return d}) // visual attribute to be updated

    d3.select('svg')
      .selectAll("text")     // select text tags to be updated
      .data(data)            // New data binded to elements
      .attr('x', function(d) {return d-20}) // placed at new positions
      .text(function(d) {return d})         // value updated
  })
```
<iframe src="recipes/updates-bar-pclick-labels.html" sandbox="allow-same-origin allow-scripts" onload="this.style.height=this.contentDocument.documentElement.scrollHeight+2+'px';"></iframe>
