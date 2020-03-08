---
layout:     post
title:      Interview Questions
subtitle:   C++
date:       2020-03-08
author:     PZ
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - C++
    - Interview
    - Leetcode
---

---

## ByteDance

**int64 check a + b > c**

#### Tips:

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/interview/1.png)

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/interview/2.png)


溢出 overflow 主要有两种：

1. a, b 同号， c 与 a, b 同号， 转化成 a > c - b
2. a, b 同号， c 与 a, b 异号：
   负数 + 负数 > 正数 return False
   正数 + 正数 > 负数 return True
3. a, b 异号，直接判断 不会溢出


```c++
bool check(int A, int B, int C)
{
    if ((A >= 0 && B <= 0>) || (A <= 0 && B >= 0>)) // A 和 Ｂ　异号
    {
        if ( A + B > C)
        {
            return true;
        }
        return false;
    }
    else　// A 和 Ｂ　同号
    {
        if ((A > 0 && C >= 0) || (A < 0 && C <= 0>>))// A 和 C 同号
        {
            if (A > C - B)
            {
                return true;
            }
            return false;
        }
        else // A 与 C 异号
        {
            if ( A > 0)
            {
                return true;
            }
            return false;
        }
    }
}

```

