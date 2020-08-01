---
layout: post
category: blog
title:  "Sliding Window Technique"
date:   2020-08-1
tags: algorithm sliding_window
image: ""
---

<a href="https://www.youtube.com/watch?v=MK-NZ4hN7rs">reference</a>

<strong>Sliding window technique</strong> improves the efficiency of iteration from O(n*k) to O(n)

### Example
Given an array of integers of size ‘n’.
Our aim is to calculate the maximum sum of ‘k’ consecutive elements in the array.

A <strong>brute Force Solution</strong> to this problem would be the following:
<pre><code><strong>int maxSum(int arr[], int n, int k) 
{ 
    </strong>// Initialize result <strong>
    int max_sum = INT_MIN; 
  </strong>
    // Consider all blocks starting with i. <strong>
    for (int i = 0; i < n - k + 1; i++) { 
        int current_sum = 0; 
        for (int j = 0; j < k; j++) 
            current_sum = current_sum + arr[i + j]; 
  </strong>
        // Update result if required. <strong>
        max_sum = max(current_sum, max_sum); 
    } 
  
    return max_sum; 
} </strong></code></pre>

<strong>Time Complexity : <i>O(n*k)</i></strong>

With <strong>sliding window technique</strong>, we can have a window of k elements and keep track of the current sum of the k element sand the maximum sum found so far. We can slide this window through the array to find the answer.

<pre><code><strong>int maxSum(int arr[], int n, int k) 
{ 
    </strong>// n must be greater <strong>
    if (n < k) { 
        cout << "Invalid"; 
        return -1; 
    } 
  </strong>
    // Compute sum of first window of size k <strong>
    int max_sum = 0; 
    for (int i = 0; i < k; i++) 
        max_sum += arr[i]; 
  </strong>
    // Compute sums of remaining windows by 
    // removing first element of previous 
    // window and adding last element of 
    // current window. <strong>
    int window_sum = max_sum; 
    for (int i = k; i < n; i++) { 
        window_sum += arr[i] - arr[i - k]; 
        max_sum = max(max_sum, window_sum); 
    } 
  
    return max_sum; 
} </strong></code></pre>

<strong>Time Complexity : <i>O(n)</i></strong>

### Uses
1. Sequentially iterate over  
    - contiguous sequence of elements
    - strings, arrays, linked list

2. To find min, max, longest, shortest, or whether contained
    - may need calculation and record some value

<li>Everything grouped <strong>sequentially</strong></li>
<li><strong>Longest/ smallest/ contains/ max/ min</strong></li>
<br><br>
<blockquote>Learn about <a href='/dyanamic-sliding-window/'>Dynamic Version</a> of Sliding Window Technique</blockquote>