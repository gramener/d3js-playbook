# Transitions

D3's selection.transition method makes it easy to animate transitions when changing the DOM. And it's very, very simple!

Say for example you want to change the color of a rectangle to red. You would normally do

```javascript
d3.select("rect").style("color", "red")
```
To instead animate the change over time, derive a transition:

```javascript
d3.select("rect").transition().style("color", "red")
```

## Add transition to bars
```javascript
d3.select("p")
  .on("click", function() {
    data = random(4)
    d3.select('svg')
      .selectAll("rect")
      .data(data)
      .transition()      // Just this single magical line
      .attr('width', function(d) {return d})

    d3.select('svg')
      .selectAll("text")
      .data(data)
      .transition()      // Just this single magical line
      .text(function(d) {return d})
      .attr('x', function(d) {return d-20})
  })
```
<iframe src="recipes/transitions-bar-pclick-labels.html" sandbox="allow-same-origin allow-scripts" onload="this.style.height=this.contentDocument.documentElement.scrollHeight+2+'px';"></iframe>

## Add duration
You can control attribute change interpolation over time by setting `duration`

```javascript
  .transition()
  .duration(1000)  // in milliseconds
```
<iframe src="recipes/transitions-duration-bar-pclick-labels.html" sandbox="allow-same-origin allow-scripts" onload="this.style.height=this.contentDocument.documentElement.scrollHeight+2+'px';"></iframe>

## Add Easing
Easing is a method of distorting time to control apparent motion in animation.

```javascript
  .transition()
  .duration(1000)  // in milliseconds
  .ease("linear")   // among cubic, poly, sin, bounce, elastic
```
<iframe src="recipes/transitions-ease-bar-pclick-labels.html" sandbox="allow-same-origin allow-scripts" onload="this.style.height=this.contentDocument.documentElement.scrollHeight+2+'px';"></iframe>

or bounce them up.

```javascript
  .transition()
  .duration(1000)
  .ease("bounce")
```
<iframe src="recipes/transitions-ease-bounce-bar-pclick-labels.html" sandbox="allow-same-origin allow-scripts" onload="this.style.height=this.contentDocument.documentElement.scrollHeight+2+'px';"></iframe>

## Add Delay
also, you could delay the transition after the event, using `.delay()`

```javascript
  .transition()
  .duration(1000)
  .delay(400)
```
<iframe src="recipes/transitions-delay-bar-pclick-labels.html" sandbox="allow-same-origin allow-scripts" onload="this.style.height=this.contentDocument.documentElement.scrollHeight+2+'px';"></iframe>
