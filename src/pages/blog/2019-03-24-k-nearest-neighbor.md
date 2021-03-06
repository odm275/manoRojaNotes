---
templateKey: blog-post
title: K-Nearest Neighbor
date: 2019-03-24T21:20:33.814Z
description: 'Introductory Algorithm to Machine Learning '
tags:
  - homework
  - machine learning
---
The K-Nearest Neighbor Algorithm compares data relative to a specific parameter, groups together the most similar data, and chooses some k sub-set of the set of data. For example, assuming we drop balls through a nail board and get a result that looks like:
```
const outputs = [
[10, 0.5, 16, 1],
[200, 0.5, 16, 4],
[350, 0.5, 16, 4],
[600, 0.5, 16, 5]
];
```
where the parameters for bounciness and ball size will be dropped for now (column 2 and column 3).

In code, we would do something like
```
const predictionPoint = 300;
const k = 3;

function distance(point){
return Math.abs(point - predictionPoint);
}

function runAnalysis(){

}

// Using lodash
_.chain(outputs)
.map(row => [distance(row[0]), row[3]])
.sortBy(row => row[0])
.slice(0, k) 
//[[50,4],[100,4],[290,1]]
.countBy(row => row[1])
// Count instances of bucket happenings // {"1":1,"4":2}
.toPairs()
.sortBy(row => row[1]) [[1,1],[4,2]]
.last()
.first()
.parseInt()
// 4th bucket had the most happenings that's closest to a drop from predictionPoint = 300
.value();
```
