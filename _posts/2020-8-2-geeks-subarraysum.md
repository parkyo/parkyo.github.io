---
layout: post
category: blog
title:  "GeeksForGeeks - Subarrays with Give Sum"
date:   2020-08-02
tags: algorithm sliding_window must_do
image: ""
---

## Problem
Given an unsorted array A of size N of non-negative integers, find a continuous sub-array which adds to a given number S.

## Solution
Sliding window technique
<pre><code><strong>int subarraySum(){
    int t, n, s;
    int cur_sum = 0, start=0, end = -1;
    cin >> t >> n >> s;
    vector<int> list(n,0);
    for(size_t j = 0; j < t; ++j){
        for(size_t i = 0; i < n; ++i){
            int cur;
            cin >> cur;
            list[i] = cur;
        }
        for(auto i : list){
            cur_sum += i;
            ++end;
            while(start <= end && cur_sum > s){
                cur_sum -= list[start];
                ++start;
            }
            if(cur_sum == s){
                cout << start+1 << " " << end+1;
                return 0;
            }
        }
    }
    
    cout << -1;
    return 0;
    
}</strong></code></pre>