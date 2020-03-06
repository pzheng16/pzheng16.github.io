---
layout:     post
title:      Leetcode DP
subtitle:   C++
date:       2020-03-04
author:     PZ
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - C++
    - Leetcode
---


# Summary

- 多状态之间得关系，**注意初始条件**
DP[i][j] iterate i or j can be reverted 
**可以反着来，可能更方便**

- **滚动数组**把循环几轮放在最开始的循环 nested cycles

- **DP 分成片段 [a,b] 应对复杂的DP问题**
学会额外增加一行一列， 作为初始值，方便计算，0，0


![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/leetcodeImg/1.png)

# Leetcode Problems

---

## Leetcode 787 Cheapest Flights Within K stops
Bellman-Ford Algorithm
```c++
 vector<int,vector<int>> BFA(K+2, vector<int> (n, cost_max);
  k = at most k intermedia points between source 
and destination
```
![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/leetcodeImg/2.png)

## Leetcode 198 213 House Robber

DP[i] **表示在1,…,i站下的最大值**

## Leetcode 309 Best Time to But and Sell Stock with cool down

**DP 用不同的数组表示当前不同的状态**
比如买股票，买进，休息，卖出
选公司，选A，选B，这样一直在这些数组间更新对大值

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/leetcodeImg/4.png)

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/leetcodeImg/3.png)

## Leetcode 790 Domino and Tromino Tiling

类似题目 **模板**
跟上面类似，**用不同状态**
**表示DP,看不同状态之间怎么转**

**堆砌模板**
**类似于fibinacci**

```c++

```

```c++
dp[0][0] = dp[1][0] = 1;
dp[0][1] = dp[1][1] = 0;
```
![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/leetcodeImg/5.png)

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/leetcodeImg/6.png)

## Leetcode 801 swap or not swap 

**两种状态，两个DP list**

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/leetcodeImg/7.png)

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/leetcodeImg/9.png)


## Leetcode 139 Word Break 

**两种状态，两个DP list**

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/leetcodeImg/10.png)

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/leetcodeImg/11.png)
