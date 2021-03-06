---
title: LeetCode 482. License Key Formatting
tags:
  - CPP
  - LeetCode
  - 字符串
  - 算法
url: 1089.html
id: 1089
categories:
  - LeetCode
date: 2017-01-13 16:26:32
---
题目描述：

> Now you are given a string S, which represents a software license key which we would like to format. The string S is composed of alphanumerical characters and dashes. The dashes split the alphanumerical characters within the string into groups. (i.e. if there are M dashes, the string is split into M+1 groups). The dashes in the given string are possibly misplaced.
>
> We want each group of characters to be of length K (except for possibly the first group, which could be shorter, but still must contain at least one character). To satisfy this requirement, we will reinsert dashes. Additionally, all the lower case letters in the string must be converted to upper case.
>
> So, you are given a non-empty string S, representing a license key to format, and an integer K. And you need to return the license key formatted according to the description above.
>
> **Example 1:**
>
> ```
> Input: S = "2-4A0r7-4k", K = 4
>
> Output: "24A0-R74K"
>
> Explanation: The string S has been split into two parts, each part has 4 characters.
>
> ```
>
> **Example 2:**
>
> ```
> Input: S = "2-4A0r7-4k", K = 3
>
> Output: "24-A0R-74K"
>
> Explanation: The string S has been split into three parts, each part has 3 characters except the first part as it could be shorter as said above.
>
> ```
>
> **Note:**
>
> 1. The length of string S will not exceed 12,000, and K is a positive integer.
> 2. String S consists only of alphanumerical characters (a-z and/or A-Z and/or 0-9) and dashes(-).
> 3. String S is non-empty.

题目说了很长，但是意思却很简单。就是把一个输入的字符串从后往前分割为K个一组，第一组可以不足K个。然后用“-”把它们连接起来。

```cpp
class Solution {
public:
    string licenseKeyFormatting(string S, int K) {
        string str;
        for(auto c : S){
            if(c == '-') continue;
            str.push_back(toupper(c));
        }
        string ans, tmp;
        int i;
        for(i = str.length(); i >= K; i -= K){
            ans = str.substr(i - K, K) + "-" + ans;
        }
        if(i > 0){
            ans = str.substr(0, i) + "-" + ans;
        }
        ans.pop_back(); // Delete "-" in the end of ans.
        return ans;
    }
};
```

