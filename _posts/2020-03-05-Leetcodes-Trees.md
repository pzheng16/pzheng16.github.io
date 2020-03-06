---
layout:     post
title:      Leetcode Trees
subtitle:   C++
date:       2020-03-04
author:     PZ
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - C++
    - Leetcode
---

<iframe width="560" height="315" src="https://www.youtube.com/embed/PbGl8_-bZxI" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<iframe width="560" height="315" src="https://www.youtube.com/embed/wmW8G8SrXDs" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


> KEY Points:

**Traversal -- Recursion --> function order --> save memory of run-time stack** :rofl:

#### 主要解决方法：

recursion + recursion ！！！！
<span style="color:red">当BFS的时候，可以queue或者两个vector,然后swap</span> :speech_balloon:

---

### Traversal - Recursion

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/trees/1.png)

### Traversal - Iteration

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/trees/3.png)

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/trees/2.png)

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/trees/4.png)

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/trees/5.png)

### Leetcode 113 Path Sum II

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/trees/6.png)

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/trees/7.png)

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/trees/8.png)

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/trees/9.png)

### Leetcode 124 Binary Tree Maximum 

:speak_no_evil:<span style="color:red">访问的过程中更新ans
ms 表示是从一个节点一直走到leaf的值，这个过程中就间接更新了</span>
每个节点的maxPathSum (这个节点是转折点）;

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/trees/10.png)

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/trees/11.png)

### Leetcode 129 Sum root to leaf numbers

**当top-down的时候就是传入argument当bottom-uP 的时候就是return value;**

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/trees/12.png)

##### BST

:two_hearts:**BST binary search tree 是 left child < root < right child **

## Leetcode 297 Serialize and Deserialize Binary Tree

**递归前序遍历，这样反过来也可以递归遍历，代码比较容易运用string流来前序遍历，因为读取之后，就会消失，很方便**

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/trees/13.png)

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/trees/14.png)

---
---

## Binary Search Tree

**添加虚头节点**
recursion
**in-order traversal BST** 就是一个排序好的vector

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/trees/15.png)

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/trees/16.png)

```c++
if(!root) return;
inorder(root->left);
do something to root:   prev = root; // 对每个节点的操作都是在这里进行；
inorder(root->right);
return;
```
```c++
BST找最小值就是一直 root -> left until it is NULL
最大值就是一直 root ->right untile it is NULL
```

### Delete Items in BST

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/trees/17.png)

##### 链表常用技巧 ！！
做有关链表的题目，有个常用技巧：**添加一个虚拟头结点：**
```c++
ListNode *head = new ListNode(-1);
```
可以简化边界情况的判断