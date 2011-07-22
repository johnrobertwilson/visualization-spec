# VIZSTRUCT 1.0

## Abstract

VIZSTRUCT is a specification for structuring data that is meant to be rendered to the end user by third party visualization libraries.

## Format

VIZSTRUCT utilizes JSON as its notation.

## Spec

### Objects

#### VIZSTRUCT Object

The container object for all of the data to be rendered. It has two members: series and options.

```
var vizstruct_object = {
  "series" : [
   {"seriesName":"series-name1", data:[[2,1], [4,2], [6,3], [3,4]]},
   {"seriesName":"series-name2", data:[['a',6], ['b',8], ['c',14], ['d',20]]}
   ],
  options:
   {"option1" : "value",
    "option2" : "value"}

};
```

### Members

#### Series

>*required
>series is an array which can contain one or multiple series elements.

```json
"series": [
     { "seriesName" : "series-name1",
       "data" : [[1, 2],[3,5.12],[5,13.1],[7,33.6],[9,85.9],[11,219.9]]},
     { "seriesName" : "series-name2",
       "data": [['a',1], ['b',2], ['c',3], ['d',4]]}
    ]
```

#### Options

>*not required
>options is an object which contains one or multiple options elements.

```json
"options" :
     {"option-name1" : "value",
      "option-name2" : "value" }

```
##### Title

>The main title of the chart. Title is an object containing optional members:

* text - The title of the chart
* align - The horizontal alignment of the title _left_ _center_ _right_
* verticalAlign - The vertical alignment of the title _top_ _middle_ _bottom_
* float - When set to true, the plot area will not move to make space for it. Defaults to false.
* color - The Hex value for the color of the title text.

```json
"options" : {
	"title": {
	"text" : "Chart title",
	"align" : "center",
	"verticalAlign" : "top",
	"color" : "#000000",
	},
}
```
##### Description

>The sub-text below the title.  Description is an object containing optional member:

* text - The description for the chart.
* color - The Hex value for the color of the description text.

```json
"options" : {
	"description": {
	"text" : "Chart description",
	"color" : "#000000",
	},
}
```

#### Legend

>The legend for the chart linking names and colors to visualized series.  Legend is an object containing the following members:

* show - Show or hide the legend, can be true or false
* position - The position of the legend in the visualization, uses compass values: n, s, e, w, nw, sw, ne, se
* color - The hex color of the font of the legend.
* background-color - The background color of the legend.

```json
"options" : {
	"legend" : {
	"show" : true,
	"color" : "#000000",
	"location" : "e",
	"backgroundColor" : "#FFFFFF",
	},
}
```

#### Series Options

>Series options is an array kept in a special subset of options called "series-options". Most third party rendering libraries separate the meta data for series into a separate subset of elements.

```json
"options" :
     { "seriesOptions:[
       { "seriesName" : "series-name1", "seriesOptions" : {"lineWidth" : 5, "color" : "#000" }},
       { "seriesName" : "series-name2", "seriesOptions" : {"startAngle" : -90, "color" : "#CCC" }} 
     ]
    ...
```

#### Plot Options

>Plot options is an object containing information about the plot area.  It contains the following members:

* background-color

```json
"options" :
     { "plotOptions": { "backgroundColor" : "#FFFFFF"},
    ...
```

#### Axes

>Options for axes are defined in the axes element of options.

```json
"options" :
     { "axes" : { "yaxis" : {"option" : "value", "option2" : "value2"},
                  "xaxis" : {"option" : "value" },
       			  "zaxis" : {"option" : "value" }
       },
     ...
```

#### Other Options

##### Colors

>An array containing the default colors for the chart's series. When all colors are used, new colors are pulled from the start again.

```json
"options" :
     { "colors" :[
		"#4572A7", 
		"#AA4643", 
		"#89A54E", 
		"#80699B", 
		"#3D96AE", 
		"#DB843D", 
		"#92A8CD", 
		"#A47D7C", 
		"#B5CA92"
	],
     ...
```

##### ToolTips
>Options object for the tooltip that appears when the user hovers over a series and points. 

Tooltip has several optional options:

* backgroudnColor - hex or rgb value
* borderColor - auto or hex or rgb value
* borderRadius - the radius of the rounded border corners
* borderWidth - width of border in pixels
* enabled - enables tooltips true or false
* shadow - Whether to apply a drop shadow to the tooltip.
* shared - When the tooltip is shared, the entire plot area will capture mouse movement, and tooltip texts for all series will be shown in a single bubble. This is recommended for single series charts and for iPad optimized sites.
* style - CSS style object for any tooltip specific styles you want

```json
"options" : {
	"tooltip": {
		"backgroundColor": "#FFF",
		"borderColor" : "auto",
		"borderRadius" : 5,
		"borderWidth" : 2,
		"enabled": true,
		"shadow": true,
		"shared": false,
		"style":
	},
}
```