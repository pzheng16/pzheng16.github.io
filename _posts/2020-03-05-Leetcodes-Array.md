---
layout:     post
title:      Leetcode Array
subtitle:   C++
date:       2020-03-04
author:     PZ
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - C++
    - Leetcode
---

- array 连续值
- array 双指针
- array 排序去除
- **array 从两边夹向中间 product of array except self**
- **array 从中间向两边散开 Longest - Palindromic Substring**
- **array也可以倒着考虑**，从后往前 --》 merge sorted aray

## Sliding windows: 固定一个增加(++),另一个不定增加

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/string/6.png)

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/string/5.png)

## Spreading from the center

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/array/1.png)

Try all possible i and find the longest palindromic string whose center is i (odd case) and i / i + 1 (even case).

