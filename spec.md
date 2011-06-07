# ZIV 1.0

## Abstract

ZIV is a specification for structuring data that is meant to be rendered to the end user by third party visualization libraries.

## Format

ZIV utilizes JSON as its notation.

## Spec

### Objects

#### Ziv Object

The container object for all of the data to be rendered. It has two members: series and options.

```
var ziv = {
  "series":[
   {"series-name1":[[2,1], [4,2], [6,3], [3,4]]},
   {"series-name2":[['a',6], ['b',8], ['c',14], ['d',20]]}
   ],
  "options":[
   {"option1":value},
   {"option2":value}
   ]
};
```

### Members

#### Series

>*required
>series is an array which can contain one or multiple series elements.

```json
"series": [
     {"series-name1":[[1, 2],[3,5.12],[5,13.1],[7,33.6],[9,85.9],[11,219.9]],
     {"series-name2":[['a',1], ['b',2], ['c',3], ['d',4]]}
    ]
```

#### Options

>*not required
>options is an array which contain one or multiple options elements.

```json
"options": [
     {"option-name1:value"},
     {"option-name2:value"}
    ]
```

##### Series Options

>*Series options is an array kept in a special subset of options called "series-options". Most third party rendering libraries separate the meta data for series into a separate subset of elements.

```json
"options": [
     {"series-options":[
      {"series-name1":[{"lineWidth":5},{"color":"#000"}]},
      {"series-name2":[{"startAngle":-90},{"color":"#CCC"}]} 
     ]}
    ]
```

##### Axes

>Options for axes are defined in the axes element of options.

```json
"options": [
     {"axes":[
      {"yaxis":[{"option":"value""}]},
      {"xaxis":[{"option":"value"}]},
      {"zaxis":[{"option":"value"}]}
     ]}
    ]
```

##### Other Available Options

* title
* description
* legend
* tooltip
* barDirection
* shadowAngle
* plotOptions