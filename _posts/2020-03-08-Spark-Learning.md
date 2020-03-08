---
layout:     post
title:      Spark Learning
subtitle:   Spark
date:       2020-03-08
author:     PZ
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - Spark
    - Big Data
---

### Transformation and Actions

- Nothing Happens when doing transformations: **map, flatmap, filter, distinct**
- Start when **doing actions**: collect, count, take, reduce, foreach

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/spark/1.png)



### Save time Example: laziness

Spark leverages this by analyzing the chain of operations before executing.

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/spark/2.png)


### Evaluation in Spark: Unlike Scala Collections !!

- **Eager and Lazy**
- **Actions and Transformations**
- **In-memory iteration**

RDDs are recomputed each time you run an action on them.

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/spark/3.png)

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/spark/4.png)

##### Cache and persist

Use persist() or cache() to cache an RDD in memory after it takes actions (like reduce())

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/spark/5.png)

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/spark/6.png)