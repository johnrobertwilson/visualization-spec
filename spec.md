# ZIV 1.0

## Abstract

ZIV is a specification for structuring data that is meant to be rendered to the end user by third party visualization libraries.

## Format

ZIV utilizes JSON as its notation.

### Objects

#### Series

*required
A series is an object which can contain one or multiple series name:value pairs. The name is the name of the series, the data array is the actual datapoints for that series. The data array can contain alphanumeric key value pairs within the main array.

series: {
  'series-name1':[[1, 2],[3,5.12],[5,13.1],[7,33.6],[9,85.9],[11,219.9]],
  'series-name2':[['a',1], ['b',2], ['c',3], ['d',4]]
}

#### Options

*not required
An object containing
