---
layout: post
category: blog
title:  "Leetcode Weekly Contest 197 - The Number of Good Pairs"
date:   2020-07-19
tags: algorithm leetcode weekly_contest map
image: ""
---

<a href = "https://leetcode.com/problems/number-of-good-pairs/">LINK</a>

### Level : Easy

## Problem
Given an array of integers nums.

A pair (i,j) is called good if nums[i] == nums[j] and i < j.

Return the number of good pairs.

## Solution
<pre><code><strong>class Solution {
public:
    
    int count(int n){
        int ans = (n + 1)*(n/2);
        if(n%2 != 0){
            ans += n/2 + 1;
        }
        return ans;
    }
    
    int numIdenticalPairs(vector&lt;int&gt;& nums) {
        int n=0;
        unordered_map&lt;int, int&gt; list;
        for (size_t i = 0; i < nums.size(); ++i){
            auto it = list.find(nums[i]);
            if(it != list.end()){
                ++(it->second);    
            }else{
                list.insert(pair&lt;int,int&gt;(nums[i],0));
            }
            
        }
        for (auto it : list){
            if(it.second > 0){
                n += count(it.second);
            }
        }
        return n;
    }
};</strong></code></pre>
<strong>Time copmlexity: <i>O(n)</i></strong>





