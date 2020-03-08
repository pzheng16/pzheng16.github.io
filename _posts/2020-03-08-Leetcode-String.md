---
layout:     post
title:      Leetcode String
subtitle:   C++
date:       2020-03-08
author:     PZ
header-img: img/post-bg-ios9-web.jpg
catalog: true
tags:
    - C++
    - Leetcode
---

> string 处理起来和 array 以及 linked list 有相同之处

- 考虑**modify in place**,内存问题
- **双指针**也能使用，快慢指针
- 从**中心**散开
- **unordered_map**， 当两个string比较的时候

##### Tips:

```c++
// check if the character contains decimals or chars
isalpha(char);//return true when var is alphabet (character) 
isdigit(char);

// uppercase to lowercase
char(tolower('A')) = 'a'
int main()
{
    char str[] = "John is from USA.";

    cout << "The lowercase version of \"" << str << "\" is " << endl;

    for (int i=0; i<strlen(str); i++)
        putchar(tolower(str[i]));
    
    return 0;
}
```

#### Leetcode 242. Valid Anagram

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/string/1.png)

##### HashMap

```c++
class Solution {
public:
    bool isAnagram(string s, string t) {
        if (s.length() != t.length()) return false;
        int n = s.length();
        unordered_map<char, int> counts;
        for (int i = 0; i < n; i++) {
            counts[s[i]]++;//default is zero 
            counts[t[i]]--;
        }
        for (auto count : counts)
            if (count.second) return false;
        return true;
    }
};
```

#### Leetcode 125. Valid Palindrome

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/string/2.png)

##### Two Pointers

```c++
// First trial, two iterations
class Solution {
public:
    bool isPalindrome(string s) {
        string newS;
        for (auto c: s)
        {
            if(isalpha(c))
            {
                newS.push_back(char(tolower(c)));
            }
            else if (isdigit(c))
            {
                newS.push_back(c);
            }
        }
        cout << newS;
        for (int i = 0, j = newS.size()-1; j-i >= 1; ++i, --j)
        {
            if (newS[i] != newS[j]) return false;
        }
        return true;
    }
};
```

In one iteration, and without new String.

```c++
class Solution {
public:
    bool isPalindrome(string s) {
        for (int i = 0, j = s.size()-1; j-i >= 1; ++i, --j)
        {
            while(!isalnum(s[i]) && i < j) ++i;
            while(!isalnum(s[j]) && i < j) --j;
            if (j - i < 1) return true;
            if (tolower(s[i]) != tolower(s[j])) return false;
        }
        return true;
    }
};
```