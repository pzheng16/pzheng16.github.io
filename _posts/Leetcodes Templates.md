---
layout:     post
title:      Leetcode模板
subtitle:   C++
date:       2019-12-16
author:     PZ
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - C++
    - Leetcode
---
# 二分模板
```
// Returns the smallest m in [l, r),
// s.t. cond(m) == True
// If not found returns r.
def binary_search(l, r, cond)
  while l < r:
    m = l + (r - l) // 2
    if cond(m):
      r = m
    else
      l = m + 1
  return l  
```
  
# 排列模板
  
  
```
def P(n, m, cur, used):
  if len(cur) == m:
    print(cur)
    return
  for i in range(n):
    if used[i]: continue
    used[i] = True
    cur.append(i + 1)
    P(n, m, cur, used)
    cur.pop()
    used[i] = False
n = 5
m = 3
P(n, m, [], [False] * n)
```
# 组合模板
```
def C(n, m, s, cur):
  if len(cur) == m:
    print(cur)
    return
  for i in range(s, n):
    cur.append(i + 1)
    C(n, m, i + 1, cur)
    cur.pop()    
n = 5
m = 3
C(n, m, 0, [])
```
# DFS
```
// Check whether there is a path from |start| to |target| in graph G.
// neighbor(x) returns the neighbors of x in G.
seen = set([start])
def dfs(n):
  if n == target:
    return True  
  for t in neighbor(n):
    if t in seen: continue
    seen.add(t)
    if dfs(t): return True
    seen.remove(t) # back-tracking  
  return False
return dfs(start)
```
# BFS
```
// Find the shortest path from |start| to |target| in a unweighted graph G.
// neighbor(x) returns the neighbors of x in G.
q = deque([start])
seen = set([start])
steps = 0
while q:
  size = len(q)
  for _ in range(size):
    n = q.popleft()
    if n == target: return steps
    for t in neighbor(n):
      if t in seen: continue
      q.append(t)
      seen.add(t)
  steps += 1
return -1 # not found
```

# 滚动数组DP模板

```
void function(N, matrix,m,n)
{
	intilize;
	vector<vector<int>> dp(...);
	for (int k = 0; k < N; ++k)// how many times
	{
		vector<vector<int>> tmp(...);
		for (int i = 0; i < m; ++i)
		{
			for (int j = 0; j < n; ++j)
			{
				/* code */
			}
		}
		dp.swap(tmp);
	}
	return ...;
}
```

# 前缀树模板

```
class Trie(object):
  def __init__(self): self.root = {}
  def insert(self, word):
    p = self.root
    for c in word:
      if c not in p: p[c] = {}
      p = p[c]
    p['#'] = True    
  def search(self, word):
    node = self._find(word)
    return node and '#' in node
    
  def startsWith(self, prefix):
    return self._find(prefix)
  def _find(self, prefix):
    p = self.root
    for c in prefix:
      if c not in p: return None
      p = p[c]
    return p
    
 ```
    
# Union Find
 
```
class UnionFindSet:
  def __init__(self, n):
    self.p = [i for i in range(n + 1)]
    self.r = [1 for i in range(n + 1)]
  def find(self, u):
    while u != self.p[u]:
      self.p[u] = self.p[self.p[u]]
      u = self.p[u]
    return u
  def union(self, u, v):
    pu, pv = self.find(u), self.find(v)
    if pu == pv: return False    
    if self.r[pu] < self.r[pv]:
      self.p[pu] = pv
    elif self.r[pu] > self.r[pv]:
      self.p[pv] = pu
    else:        
      self.p[pv] = pu
      self.r[pu] += 1
    return True
 ```
