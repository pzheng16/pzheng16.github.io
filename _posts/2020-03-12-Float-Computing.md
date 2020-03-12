---
layout:     post
title:      Float Computing
subtitle:   C++/C
date:       2020-03-12
author:     PZ
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - C++
    - Float
    - Fundamentals
---

## Representation

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/float/1.png)

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/float/2.png)

## Keys:

#### 0.1 vs 0.5
0.1 不能被完全表示；因为十进制的0.1换算成二进制是一个无限循环小数
0.5 可以
因为是二进制的小数 2 的 -1 次方

#### float == float ??

由于浮点数存在运算误差，所以比较两个浮点数是否相等常常会出现错误的结果。正确的比较方法是判断**两个浮点数之差的绝对值是否小于一个很小的数**

如果参与运算的两个数其中一个是整型，那么整型可以自动提升到浮点型号.

浮点数常常无法精确表示，并且浮点数的运算结果可能有误差；

比较两个浮点数通常比较它们的绝对值之差是否小于一个特定值；

整型和浮点型运算时，整型会自动提升为浮点型；

可以将浮点型强制转为整型，但超出范围后将始终返回整型的最大值。