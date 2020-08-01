---
layout: post
category: blog
title:  "Sliding Window Technique with Dynamic Variant"
date:   2020-08-01
tags: algorithm sliding_window 
image: ""
---

<a href='/sliding-window/'>reference</a>

## Example

### Problem 1
Find the <strong>smallest subarray</strong> with given sum

### Solution
As you iterate through the array, move the start of the window to the left while the sum of the window elements is still bigger than or equal to the targetSum.

<pre><code><strong>int smallestSubarray(int targetSum, vector&lt;int&gt; arr) 
{ 
    int start = 0;
    int cur_sum = 0;
    int min_size = INT_MAX;
    for (int i = 0; i < arr.size(); ++i){
        cur_sum += arr[i];
        while(cur_sum >= targetSum){
            min_size = min(min_size, i - start + 1);
            cur_sum -= arr[start];
            ++start;
        }
    }
    return min_size;
} </strong></code></pre>

<strong>Time Complexity : <i>O(n^2)</i></strong>

### Problem 2
Find the <strong>longest substring</strong> length with K distinct characters

### Solution
Similar to the solution to the previous problem. 
Keep track of the number of each distinct character in a hashmap and check the size of the hashmap to see if you have violated the required number of characers.

<pre><code><strong>int longestSubstr(int k, string& s){
    int start = 0, max_size = 0;
    unordered_map&lt;char, int&gt; map;
    for (char c : s){
        auto it = map.find(c);
        if(it != map.end()){
            ++(it->second);
        }else{
            map.insert(pair&lt;char,int&gt;(c, 1));
        }
        while(map.size() > k){
            auto it2 = map.find(s[start]);
            if((it2->second) == 1){
                map.erase(it2);
            }else{
                --(it2->second);
            }
            ++start;
        }
        if(max_size < map.size()){
            max_size = map.size();
        }
    }
    return max_size;
}</strong></code></pre>
