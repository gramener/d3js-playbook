# Cascading Style Sheets

CSS syntax consists of a collection of *styles or rules*. Each *style* consists of a *selector* and a *declaration block*. The *selector* determines to which HTML elements the style is applied. The *declaration block* is composed of a sequence of *property-value pairs* gruped in curly brakets. The property and it's value is separated by a colon (`:`), and *property-value pairs* are separated from each other by a semi-colon (`;`).

```css
body {
  background: white;
  color: black;
}
```
## Styling SVG with CSS

Previous example where we created shapes can be styled using CSS selectors.
HTML code

```html
<svg width="200" height="200" id="parent">
  <circle cx="25" cy="25" r="20" class="ball"/>
  <ellipse cx="75" cy="25" rx="50" ry="20" class="ball"/>
  <rect x="25" y="25" width="40" height="80" class="pad"/>
  <text x="100" y="100">Magic!</text>
  <path d="M100 100 L50 200 L150 200 Z"/>
</svg>
```
CSS code

```css
#parent {
  border:1px solid #000;
}
.ball {
  fill: red;
}
ellipse.ball {
  stroke: black;
}
.pad {
  fill: blue;
}
text {
  font-size: 12px;
  text-decoration: underline;
}
path {
  opacity: 0.3;
  stroke-width: 5px;
  stroke: red;
}
```
<iframe src="http://jsbin.com/gukaki/embed?html,css,output" style="border: 1px solid rgb(170, 170, 170); width: 100%; min-height: 450px; height: 30px;"></iframe>

In effect, we have applied styles to multiple elements. And, CSS is easier to read and maintian.
