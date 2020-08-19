---
layout: post
category: blog
title:  "Leetcode - Find Kth Positive Number"
date:   2020-08-11
tags: algorithm must_do leetcode
image: ""
---
<a href="https://practice.geeksforgeeks.org/problems/lru-cache/1">link</a>

## Problem
Given an array arr of positive integers sorted in a strictly increasing order, and an integer k.
Find the kth positive integer that is missing from this array.

## Solution 1
Use binary search to find the gap where the Kth missing number exists
1. <code>arr[i-1] = i</code>
2. <strong>[ l ,  r )</strong>
3. <code>m-1</code> is the midpoint of the subarray in the binary search
<pre><code><strong>int findKthPositive(vector&lt;int&gt;& arr, int k) {
    size_t l = 0, r = arr.size();
    while(l < r){
        size_t m = (l + r + 1)/2 ;
        if(arr[m-1] - m < k){
            l = m;
        }else{
            r = m-1;
        }
    }
    </strong><i>//(l-1) + 1 + k</i><strong>
    return l + k;
}
</strong></code></pre>
<strong>Time Complexity : <i>O(logn)</i></strong>

## Solution 2
<pre><code><strong>int findKthPositive(vector&lt;int&gt;& arr, int k) {
        int count = arr[0]-1;
        size_t i = 1;
        while(i < arr.size() && count < k){
            count += arr[i]-arr[i-1]-1;
            ++i;
        }
        if (count >= k){
            return i-1 + k;
        }
        return i + k;
}
</strong></code></pre>
<strong>Time Complexity : <i>O(n)</i></strong>