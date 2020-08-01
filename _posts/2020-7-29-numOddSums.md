---
layout: post
category: blog
title:  "Leetcode Biweekly Contest 30 - Number of Subarrays with Odd Sums"
date:   2020-07-29
tags: algorithm leetcode biweekly_contest 
image: ""
---

<a href = "https://leetcode.com/problems/number-of-sub-arrays-with-odd-sum/">LINK</a>

### Level : Medium

## Problem
Given an array of integers arr. Return the number of sub-arrays with odd sum.

As the answer may grow large, the answer must be computed modulo 10^9 + 7.

 

## Solution
1. Keep track of the number of subarrays of odd sums and even sums. 
2. If the element is odd, swap odd and even and increment odd
3. If the element is even, increment even
4. Add the number for every element to the sum
<pre><code><strong>int numOfSubarrays(vector&lt;int&gt;& arr) {
      int odd = 0, even = 0, sum = 0;
      for(auto a : arr){
          if(a % 2 == 1){
              swap(odd, even);
              ++odd;
          }else{
              ++even;
          }
          sum += odd;
      }
      return sum % 10000000007;
  }</strong></code></pre>
<strong>Time copmlexity: <i>O(n)</i></strong>
