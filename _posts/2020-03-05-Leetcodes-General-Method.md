---
layout:     post
title:      Leetcode General
subtitle:   C++
date:       2020-03-04
author:     PZ
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - C++
    - Leetcode
---


**Sort** 通常能做到 NlogN 如果time exceed，可以尝试先sort，再做处理

超时的时候都想着把**重要步骤时间复杂度降低**
比如改用**Map Find** 而不是 **Vector Count**

	• 通常提到O(1) find 第一想到的是Map
	• 提到 O(1) 修改某个元素的位置，那就是Linked List 
	§ 经典例题：LRU cache = Double Linked List + HashMap

**记录的数都很有意义**，length等等尤其在array里面


```c++ 
a + 0ll + b// 防止溢出
``` 

##### 二分法

```c++  
通常 while (x < y) 求 x = y 那个时候的值。 
可以用来求upper bound 或者 Lower bound --> 
LeetCode 278. First Bad Version
```


```c++
typedef pair<int,char> pi;
```

##### 需要最大最小值

当需要找到**最小值或者最大值**的时候，就不需要一个一个遍历了，用**heap**去实现 （**multiset， multimap**) 等等。

<img src="http://wx2.sinaimg.cn/large/006m97Kgly1ftmb1yc189j30v90usq66.jpg" width="500" height="500" />