---
layout:     post
title:      Leetcode Recursion
subtitle:   C++
date:       2020-03-06
author:     PZ
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - C++
    - Leetcode
---

### Tips:

**Linked list，或者Tree Search或者一层一层的推导之类的，依靠前一层的推导 的题目常用 recursion （tree 一定要用递归的思想）**
首先把函数的功能定义：假想这个会返回什么
然后利用子序列函数的结果进行处理，获得现在序列的函数结果。


**双重 recursion 假设两个recursion**，一个返回所有可能的； 一个返回当前节点是起点的可能性。

### Leetcode 437 Path Sum III

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/recursion/1.png)

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/recursion/2.png)

### Recursion Templates

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/recursion/3.png)

#### Tail Recursion

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/recursion/4.png)

Tail recursion is a recursion where the recursive call is the final instruction in the recursion function. And there should be only one recursive call in the function

The benefit of having tail recursion is that it could avoid the accumulation of stack overheads during the recursive calls, since the system could reuse a fixed amount space in the stack for each recursive call. 

**好处是Runtime stack 每次回归都是固定的，用一个函数就可以描述直接就return 到当前 stack！！！**

C, C++ support the optimization of tail recursion functions. On the other hand, Java and Python do not support tail recursion optimization.

```c++
unsigned int f( unsigned int a ) {
   if ( a == 0 ) {
      return a;
   }
   return f( a - 1 );   // tail recursion
}
```