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

**不要在一行写判断函数**
如下面：会出错！！！！
```c++
if(needle[k] != haystack[j-nSize+1+k]) allSame = false; break;
```

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

<img src="http://wx2.sinaimg.cn/large/006m97Kgly1ftmb1yc189j30v90usq66.jpg" width="200" height="200" />

##### C++ map 自动生成，比如 char, int 自动为 0 的value,可以直接 count[t[i]]++


```c++
unordered_map<char, int> counts;
for (int i = 0; i < n; i++) {
	counts[s[i]]++;
	counts[t[i]]--;
}
```