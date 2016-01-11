# JavaScript
JavaScript is a cross-platform, object-oriented scripting language. It is a small and lightweight language. Inside a host environment (for example, a web browser), JavaScript can be connected to the objects of its environment to provide programmatic control over them.

## Developer tools
The DevTools provide web developers deep access into the internals of the browser and their web application. Using the DevTools, we can efficiently track down layout issues, set JavaScript breakpoints, and get insights for code optimization.

In case of Chrome, you can

* Select `More Tools > Developer Tools` from the Menu. or,
* Right-click on a page element and select Inspect. or,
* Use `Ctrl+Shift+I`

to open the devtools.

**Elements window**
![devtools window](./assets/devtools-window.png)
**Console**
![devtools javascript console](./assets/devtools-js-console.png)

## Data representation
You can represent data in JS with Arrays or Objects.

### Arrays
```javascript
var numbers = [1, 3, 5, 7, 9]
var text = ["data", "d3", "dom"]

numbers[2]   // returns 5
text[2]      // returns "dom"
```

### Objects
```javascript
var car = {
  make: "Ford",
  model: "Mustang",
  year: 1969
}
```
or
```javascript
var car = new Object()  // or var car = {}
car.make = "Ford"
car.model = "Mustang"
car["year"] = 1969      // or car.year = 1969
```
You can access data in an object by referencing its properties
```javascript
car.make       \\ returns "Ford"
car["make"]    \\ returns "Ford"
```

### Data Structures

You could combine objects and arrays to generate arrays of objects, or objects of arrays, or objects of objects or whatever suits for your data.
```javascript
var solar = {
  earth: [{USA: 180}, {India: 100}],
  mars: [{Alien: -0.5}]
}

solar.earth[0].USA  // returns 180
```
