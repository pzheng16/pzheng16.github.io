---
layout:     post
title:      Leetcode Linked Lists
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

**linked list排序 想到 while 以及 priority_queue**

### Leetcode 23 Merge K Sorted lists

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/linkedlist/1.png)

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/linkedlist/2.png)

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/linkedlist/3.png)

**如果想知道前后两个linked node, 可以用 cur->next 进行比较，这样就cur 和 cur->next 都能知道而不需要prev 和 cur 两个了**

### Merge Sort

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/linkedlist/5.png)

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/linkedlist/4.png)

##### Templates:

```c++
sort(A)
{
	a1 = first half of A;
	a2 = second half of A;
	return merge(sort(a1),sort(a2));
	
}

function merge(…) {…}

///////////////////////
ListNode* merge(ListNode* l1, ListNode* l2) {
    ListNode dummy(0);
    ListNode* tail = &dummy;
    while (l1 && l2) {
      if (l1->val > l2->val) swap(l1, l2);
      tail->next = l1;
      l1 = l1->next;
      tail = tail->next;
    }
    tail->next = l1 ? l1 : l2;    
    return dummy.next;
  }
```

