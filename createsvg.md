# Creating SVG

If we remember the svg structure

```html
<svg width="100" height="50" style="background: red;">
</svg>
```
<svg width="100" height="50" style="background: red;">
</svg>

We could create the same like:

```javascript
d3.select("body")
  .append("svg")
  .attr("width", 100)
  .attr("height", 50)
  .style("background", "red")
```

<iframe src="http://jsbin.com/xujaro/embed?js,output" style="border: 1px solid rgb(170, 170, 170); width: 100%; min-height: 200px; height: 30px;"></iframe>

Another approach, we could get attribute values from Object like:

```javascript
var viz = {width: 250, height: 50, background: "red"}

var svg = d3.select("body")
            .append("svg")
            .attr("width", viz.width)
            .attr("height", viz.height)
            .style("background", viz.background)
```

## Enter data

How about adding shapes to svg?

Let's take circles with varying radii, and add them to the svg

```javascript
var radius = [5, 10, 15, 20]

var circles = svg.selectAll("circle")
                 .data(radius)
                 .enter()
                 .append("circle")

circles.attr("cx", function(d) { return 10*d})
       .attr("cy", 25)
       .attr("r", function(d) { return d})
```

<iframe src="http://jsbin.com/bahewe/embed?js,output" style="border: 1px solid rgb(170, 170, 170); width: 100%; min-height: 300px; height: 30px;"></iframe>
