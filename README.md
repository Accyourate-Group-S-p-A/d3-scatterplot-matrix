# d3-scatterplot-matrix

a reusable D3.js scatterplot plugin that supports easy customization

this plugin is implemented as a closure that supports [method chaining](https://en.wikipedia.org/wiki/Method_chaining)

[why implement the plugin as a closure (by Mike Bostock)](https://bost.ocks.org/mike/chart/)

## Dependency

- D3.js (5.x version)

## Installing

first, download [d3.scatterplotMatrix.js](d3.scatterplotMatrix.js)

d3.scatterplotMatrix.js can be loaded directly as

```html
<script src="pathToTheFile/d3.scatterplotMatrix.js"></script>
```

then use as

```js
let chart = d3.scatterplotMatrix()
```

or if you are using Node.js/CommonJS

```js
import scatterplotMatrix from "pathToTheFile/d3.scatterplotMatrix.js"
```

## Usage example

```js
let data = [{x: 10, y: 10, z: 4}, {x: 20, y: 15, z: 6}, {x: 30, y: 0, z: 1}]

let chart = d3.scatterplotMatrix()
    .traits(['x', 'y', 'z'])

let svg = d3.select('body').append('svg')
    .datum(data)
    .call(chart)
```

Another example of visualizing the Iris Dataset can be seen [here](https://zhangyu94.github.io/d3-scatterplot-matrix)

## How to customize

```js
// create a scatterplotMatrix closure
let chart = d3.scatterplotMatrix()

// set width
chart.width(800)

// get width
let width = chart.width() /* width = 800 */

// other attributes in the API can be get/set similarly
```

## API Reference

- width: [Number]
    - get/set the width of the whole chart
    - default = 800
- height: [Number]
    - get/set the height of the whole chart
    - default = 800
- padding: [Number]
    - get/set the padding between each scatterplot
    - default = 20
- margin: [{left: Number, right: Number, top: Number, bottom: Number}]
    - get/set the margin  
    - default = {left: 10, right: 100, top: 0, bottom: 0})
- duration: [Number]
    - get/set the transition duration (ms)
    - default = 500
- traits: [Array(String)]
    - get/set the array of attribute names
    - default = null
- colorValueMapper: [Function]
    - get/set the access method to the value that has a one-to-one mapping with the filling color
    - default = d => d.label
- rValueMapper: [Function]
    - get/set the access method to point radius
    - default = _ => 3
    - by default radius = 3 for all the points
- strokeValueMapper: [Function]
    - get/set the access method to point stroke color
    - default = _ => "black"
    - by default stroke_color = "black" for all the points
- drawLegend: [Boolean]
    - get/set whether legend should be drawn
    - default = false
- enableBrush: [Boolean]
    - get/set whether brushing should be enabled
    - default = true
    - note: at most one of brushing and and zooming function can be enabled
- enableZoom: [Boolean]
    - get/set whether zooming should be enabled
    - default = true
    - note: at most one of brushing and and zooming function can be enabled
- zoomMode: [String]
    - get/set the mode of zooming in ["filterAxis", "filterData"]
    - default = "filterAxis"
    - note: in "filterAxis" mode, only the two brushed traits would update to the brushed range;
        in "filterData" mode, the range of all the axis would update to fit the range of filtered data
- labelMode: [String]
    - get/set the mode of trait label in ["diagonal", "all"]
    - default = "diagonal"
    - note: in "filterAxis" mode, only the diagonal scatter plots have trait labels;
        in "all" mode, all the scatter plots have trait labels
- tickLabelMode: [String]
    - get/set the mode of tick value label in ["side", "all"]
    - default = "side"
    - note: in "side" mode, only the left side and bottom side of the scatter plot matrix show value labels;
        in "all" mode, all the scatter plots have their own value labels

## Credit

This scatterplot matrix is based on the [scatterplot matrix implementation](https://bl.ocks.org/mbostock/4063663) by Mike Bostock
