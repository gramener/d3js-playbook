# Reading files

D3 has a bunch of filetypes it can support when loading data. Such as `d3.text` for plain text, `d3.json` for JSON, `d3.xml` for XML, `d3.html` for HTML, `d3.csv` for comma-separated values, and `d3.tsv` for tabulation-separated values.

Most commonly we would use use  `d3.csv` or `d3.json`.

Let's say you have a csv with some countries data `countries.csv`

```hmtl
country,gold,silver
USA,10,20
China,20,100
India,200,50
Russia,25,80
Germany,10,200
UK,150,75
France,10,75
UAE,30,150
Canada,100,15
```
Use `d3.csv` to convert it into an array of objects

```javascript
d3.csv("countries.csv", function(data) {
  console.log(data)    // print array of objects
  console.log(data[0]) // print first country
  DoSomeMagic(data)    // pass this data to render
})
```

```javascript
> console.log(data)
  [Object, Object, Object, Object, Object, Object, Object, Object, Object]
> console.log(data[0])
  Object {country: "USA", gold: "10", silver: "20"}
```

As you see, headers of the CSV have been used as the property names for the data objects.

But, values associated with these properties are all strings!

```javascript
d3.csv("countries.csv",  function(d) {
  return {
    country : d.country,
    gold : +d.gold,
    silver : +d.silver
  };
}, function(data) {
  console.log(data[0])
})
```

```javascript
> console.log(data[0])
Object {country: "USA", gold: 10, silver: 20}
```

Or store data in global variable and call functions

```javascript
var dataset

d3.csv("countries.csv", function(data) {
  dataset = data
  print1()
})

function print1() {
  console.log(dataset[0])
}
```

## Scatterplot from data.csv

```javascript
var svg = d3.select("body")
              .append("svg")
              .attr("width", 250)
              .attr("height", 250)

d3.csv("countries.csv", function(data) {
  svg.selectAll("circle")
     .data(data).enter()
     .append("circle")
     .attr("cx", function(d) {return d.gold})
     .attr("cy", function(d) {return d.silver})
     .attr("r", 4)
})
```
<iframe src="recipes/files-scatter.html" sandbox="allow-same-origin allow-scripts" onload="this.style.height=this.contentDocument.documentElement.scrollHeight+2+'px';"></iframe>
