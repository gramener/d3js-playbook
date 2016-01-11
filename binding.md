# Data Binding

In D3, we can bind the data to HTML elements in the DOM. Something like associating, data (defined in JavaScript) to elements, which can later be referenced to do operations.

## Bind
```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>D3 Binding</title>
  <script src="//d3js.org/d3.v3.min.js"></script>
</head>
<body>
<script>
var data = [1, 2, 3, 4]
d3.select("body")     // select the body
  .selectAll("p")     // empty <p> selections to be used later
  .data(data)         // parses data, and runs below operations n times
  .enter()            // creates new data-bound element
  .append("p")        // append <p> tag for each datum
  .text("I'm no. 1")  // changes attribute's value
</script>
</body>
</html>
```
<iframe src="http://jsbin.com/fukejuc/embed?html,output" style="border: 1px solid rgb(170, 170, 170); width: 100%; min-height: 300px; height: 30px;"></iframe>

## Custom function
```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>D3 Binding</title>
  <script src="//d3js.org/d3.v3.min.js"></script>
</head>
<body>
<script>
var data = [1, 2, 3, 4]
d3.select("body")
  .selectAll("p")
  .data(data)
  .enter()
  .append("p")
  .text(function(d) {return "I'm no " + d}) // custom function
</script>
</body>
</html>
```
<iframe src="http://jsbin.com/nixuto/embed?html,output" style="border: 1px solid rgb(170, 170, 170); width: 100%; min-height: 300px; height: 30px;"></iframe>

## OddEven?
```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>D3 Binding</title>
  <script src="//d3js.org/d3.v3.min.js"></script>
</head>
<body>
<script>
var data = [1, 2, 3, 4]
d3.select("body")
  .selectAll("p")
  .data(data)
  .enter()
  .append("p")
  .text(function(d) {return "I'm no " + d})
  .style("color", function(d) {
    if (d%2 == 0) { return "red" }  // if even
   })
</script>
</body>
</html>
```
<iframe src="http://jsbin.com/kejefo/embed?html,output" style="border: 1px solid rgb(170, 170, 170); width: 100%; min-height: 300px; height: 30px;"></iframe>
