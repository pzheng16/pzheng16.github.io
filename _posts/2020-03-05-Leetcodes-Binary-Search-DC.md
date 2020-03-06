---
layout:     post
title:      Leetcode Binary Search & Divide and Conquer
subtitle:   C++
date:       2020-03-05
author:     PZ
header-img: img/post-bg-keybord.jpg
catalog: true
tags:
    - C++
    - Leetcode
---

<iframe width="560" height="315" src="https://www.youtube.com/embed/v57lNF2mb_s" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<iframe width="560" height="315" src="https://www.youtube.com/embed/J-IQxfYRTto" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/BinarySearch/1.png)

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/BinarySearch/2.png)

- **Template寻找最小的值满足 g(m)---二分核心思想 --- 记住**

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/BinarySearch/3.png)

---

### Leetcode 35 Search Insert Position

**int m = 0 out of the while loop save more memory usage**

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/BinarySearch/4.png)


### 二分法总结 

https://www.cnblogs.com/grandyang/p/6854825.html
二分搜索总结
如果需要对边缘元素 Array[r] 进行判断就要用闭合区间[l,r]


### Leetcode 33, 81 Search in Rotated Sorted Array

通过二分法判断哪个部分是有序的
因为需要比较nums[r]，所以用闭合区间

**search in Rotated Sorted Array 2**
```c++
if (nums[mid] == nums[r]) r --;
```
![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/BinarySearch/5.png)

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/BinarySearch/6.png)

- **二分法查找最小值所在的index 这个只针对 rotated stored array**

- **当需要访问right 的时候就需要用闭合区间**

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/BinarySearch/7.png)

---

### Leetcode 852 Peak Index in Mountain Array

using the template for **upper bound**
```c++
A[m] > A[m+1]
```

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/BinarySearch/8.png)

### Leetcode 153 Find Minimum in Rotated Sorted Array

 ##### Divide and Conquer && Binary Search --- think both of them

 ![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/BinarySearch/9.png)

 ![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/BinarySearch/11.png)

 ![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/BinarySearch/10.png)

 ### Leetcode 154 Find Minimum in Rotated Sorted Array II

 ![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/BinarySearch/12.png)


### Leetcode 162 Find Peak Element 

**时刻保持l会大于左边值，r会大于右边值**

 ![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/BinarySearch/13.png)

  ![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/BinarySearch/14.png)

