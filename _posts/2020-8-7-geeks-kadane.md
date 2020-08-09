---
layout: post
category: blog
title:  "GeeksForGeeks - Kadane's algorithm"
date:   2020-08-07
tags: algorithm must_do kadane
image: ""
---

## Problem
Given an array arr of N integers. Find the contiguous sub-array with maximum sum.


## Solution
I used 2D array with bottom-top DP approach iniitally. 
However, I figured that I only need 1D array and as iterating through, it only matters what the best sum is until the previous index for the current index since it is supposed to be contiguous.
<pre><code><strong>int kadane() {
    int t, n;
    cin >> t;
    while(t > 0){
        cin >> n;
        int list[n]={0};
        int max = INT_MIN;
        size_t i = 0;
        while(i < n){
            int cur;
            cin >> cur;
            list[i] = cur;
            ++i;
        }
        for(size_t i = 1; i < n; ++i){
            list[i] = max(list[i], list[i]+list[i-1]);
            max = max(max, list[i]);
        }
        --t;
        cout << max << endl;
    }
    return 0;
}</strong></code></pre>