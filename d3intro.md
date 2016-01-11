# D3.js Basics

Visit the project web site at [d3js.org](http://d3js.org/).

D3.js is a JavaScript library for manipulating documents based on data. D3 helps you bring data to life using HTML, SVG, and CSS.

## Adding elements

Here's how we can add a new paragraph in the DOM.

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>D3: Add Elements</title>
  <script src="//d3js.org/d3.v3.min.js"></script>
</head>
<body>
<script>
d3.select("body")  // select the <body> tag
  .append("p")     // create and append a <p> tag
  .text("Eureka!") // set text content
</script>
</body>
</html>
```

<iframe src="http://jsbin.com/yodeqo/embed?js,output" style="border: 1px solid rgb(170, 170, 170); width: 100%; min-height: 200px; height: 30px;"></iframe>

## Changing Attributes

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>D3: Change Attributes</title>
  <script src="//d3js.org/d3.v3.min.js"></script>
</head>
<body>
  <p>I'm already here</p>
<script>
d3.select("p")                // select <p> tag
  .style("font-size", "24px") // change font-size to 24px
  .style("color", "red")      // change color to red
</script>
</body>
</html>
```

<iframe src="http://jsbin.com/kiyoho/embed?html,output" style="border: 1px solid rgb(170, 170, 170); width: 100%; min-height: 300px; height: 30px;"></iframe>

## Chaining

Chaining helps you to perform several actions in a single line of code. But, at times, you need to break the chain, to work on individual parts.

```javascript
d3.select("body")
  .append("p")
  .text("Eureka!")
```
Can be rewritten as

```javascript
var body = d3.select("body")
var p = body.append("p")
p.text("Eureka!")
```

## Selectors

D3.js uses CSS3 selectors to identify elements. After selecting elements, you can apply operators to them.

You've two top-level methods for selecting elements. `d3.select` and `d3.selectAll`

**d3.select** only the first matching element.

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>d3.select</title>
  <script src="//d3js.org/d3.v3.min.js"></script>
</head>
<body>
  <p>Alpha</p>
  <p>Beta</p>
  <p>Gamma</p>
<script>
d3.select("p")  // select first <p>
  .style("font-size", "24px")
  .style("color", "red")
</script>
</body>
</html>
```
<iframe src="http://jsbin.com/nagoge/embed?html,output" style="border: 1px solid rgb(170, 170, 170); width: 100%; min-height: 300px; height: 30px;"></iframe>

**d3.selectAll** selects all matching elements in document traversal order.

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>d3.selectAll</title>
  <script src="//d3js.org/d3.v3.min.js"></script>
</head>
<body>
  <p>Alpha</p>
  <p>Beta</p>
  <p>Gamma</p>
<script>
d3.selectAll("p")  // select all <p>
  .style("font-size", "24px")
  .style("color", "red")
</script>
</body>
</html>
```
<iframe src="http://jsbin.com/juzili/embed?js,output" style="border: 1px solid rgb(170, 170, 170); width: 100%; min-height: 300px; height: 30px;"></iframe>
