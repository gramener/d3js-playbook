# Data Manipulations

When using D3—and doing data visualization in general—you tend to do a lot of array manipulation. You could use [array methods built-in to JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/prototype), look for [D3 Array utilities](https://github.com/mbostock/d3/wiki/Arrays) or go for Underscore.js or Lo-Dash for JavaScript utility libraries.

But, for basics, mostly if you're only looking to filter the data.

Say plot `countries.csv` where gold > 100.

```javascript
// data => countries.csv
data = data.filter(function (d) {return (d.gold > 100) })
console.log(data) // returns India and UK

// Previous scatterplot function comes below
```
<iframe src="recipes/filter-data-scatter.html" sandbox="allow-same-origin allow-scripts" onload="this.style.height=this.contentDocument.documentElement.scrollHeight+2+'px';"></iframe>

## Use d3.filter
```javascript
// apply filter after appending circles
svg.selectAll("circle")
   .data(data).enter()
   .append("circle")
   .filter(function(d) { return d.gold > 100 })
   // attr(..., ...)
```
<iframe src="recipes/filter-d3-scatter.html" sandbox="allow-same-origin allow-scripts" onload="this.style.height=this.contentDocument.documentElement.scrollHeight+2+'px';"></iframe>

## array.filter() vs d3.filter()

Notice the visual differences in two approaches?

* Check DOM
* Check Scales
* And, labels
