---
layout: post
category: blog
title:  "Leetcode Weekly Contest 197 - The Number of Substrings with 1's"
date:   2020-07-19
tags: algorithm leetcode weekly_contest 
image: ""
---

<a href = "https://leetcode.com/problems/number-of-substrings-with-only-1s/">LINK</a>

### Level : Medium

## Problem
Given a binary string s (a string consisting only of '0' and '1's).

Return the number of substrings with all characters 1's.

Since the answer may be too large, return it modulo 10^9 + 7..

## Solution
<pre><code><strong>class Solution {
public:
    unsigned long long count(unsigned long long n){
        unsigned long long ans = (n + 1)*(n/2);
        if(n%2 != 0){
            ans += n/2 + 1;
        }
        return ans;
    }
    
    int numSub(string s) {
        unsigned long long ans = 0;
        int num = 0;
        for (auto c : s){
            if (c == '1'){
                ++num;
            }else{
                ans += count(num);
                num = 0;
            }
        }
        ans += count(num);
        return ans % (unsigned long long)(pow(10,9) + 7);
    }
};</strong></code></pre>
<strong>Time copmlexity: <i>O(n)</i></strong>





