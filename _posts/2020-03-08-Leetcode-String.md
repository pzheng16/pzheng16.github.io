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
isalnum(char);// check the character is the number or alphabet

string ans = "a";
ans += '0' + 26;
// string can use = 

// Substr
s.substr(i, 10)
// start from position i, with 10 characters

// string to int
string s = stoi("123")//123

//char to int
char c = '0' + 20;
int num = '20' - '0';

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


#### Leetcode 28. Implement strStr()

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/string/3.png)

##### Hash(char) --> Rabi-Karp Algorithm

```c++
class Solution {
public:
    int strStr(string haystack, string needle) {
        int nSize = needle.size();
        int hSize = haystack.size();
        if (nSize > hSize) return -1;// if needle size is larger, then return -1
        int ini = 0;
        int nSum = 0;
        for (int i = 0; i < nSize; ++i)
        {
            ini += haystack[i] - '0'; // calculate the initial sum of hash(char) (needle size)
            nSum += needle[i] - '0';// calculate the initial sum of needle hash(char) 
        }
        for (int j = nSize-1; j < hSize; ++j)
        {
            if (j >= nSize)// update initial sum by substracting the first one, and adding a new one at the end
            {
                ini = ini - (haystack[j-nSize]-'0') + (haystack[j]-'0');
            }
            if (ini == nSum)// compara characters one by one only when hash sums are the same
            {
                bool allSame = true;
                for(int k = 0; k <= nSize-1; ++k)
                {
                    if(needle[k] != haystack[j-nSize+1+k])
                    {
                        allSame=false;
                        break;
                    }
                }
                if (allSame) return j-nSize+1;
            }
        }
        return -1;
        
    }
};
```



#### Leetcode 38. Count and Say

![img](https://raw.githubusercontent.com/pzheng16/pzheng16.github.io/master/img/string/4.png)

##### Two Pointers: 
one points to the beginning. the other points to the current one.

```c++
// Author: Huahua, 4 ms, 8.6 MB
class Solution {
public:
  string countAndSay(int n) {
    string ans = "1";
    for (int i = 1; i < n; ++i)
      ans = say(ans);
    return ans;
  }
private:
  string say(const string& n){
    string ans;
    int s = 0, l = n.length();
    // two pointers, s points to the beginning, e points to the current one.
    for (int e = 1; e <= l; ++e)
      if (e == l || n[s] != n[e]) {
        int count = e - s;
        ans += '0' + count;
        ans += n[s];
        s = e;
      }
    return ans;
  }
};
```