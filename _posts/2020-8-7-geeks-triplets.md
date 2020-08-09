---
layout: post
category: blog
title:  "GeeksForGeeks - Count Triplets"
date:   2020-08-07
tags: algorithm must_do
image: ""
---

## Problem
Given an array of distinct integers. The task is to count all the triplets such that sum of two elements equals the third element.

## Solution
<pre><code><strong>int triplets(){
    int t, n;
    cin >> t;
    while(t > 0){
        cin >> n;
        vector<int> list(n);
        int count = 0;
        size_t i = 0;
        while(i < n){
            int cur;
            cin >> cur;
            list[i] = cur;
            ++i;
        }
        sort(list.begin(), list.end());
        for(size_t i = n-1; i >= 0; --i){
            size_t j = 0, k = i-1;
            while(j < k){
                int sum = list[j] + list[k];
                if(sum == list[i]){
                    ++count;
                }else if(sum > list[i]){
                    --k;
                }else{
                    ++i;
                }
            }
        }
        if(count > 0){
            cout << count << endl;
        }else{
            cout << -1 << endl;
        }
        --t;
    }
    return 0;
}</strong></code></pre>