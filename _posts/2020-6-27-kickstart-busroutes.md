---
layout: post
category: blog
title:  "Google Kick Start 2020 Round B - Bus Routes"
date:   2020-06-27
tags: algorithm kick_start stack
image: ""
---

<a href = "https://codingcompetitions.withgoogle.com/kickstart/round/000000000019ffc8/00000000002d82e6">LINK</a>

## Problem
Bucket is planning to make a very long journey across the countryside by bus. Her journey consists of N bus routes, numbered from 1 to N in the order she must take them. The buses themselves are very fast, but do not run often. The i-th bus route only runs every Xi days.

More specifically, she can only take the i-th bus on day Xi, 2Xi, 3Xi and so on. Since the buses are very fast, she can take multiple buses on the same day.

Bucket must finish her journey by day D, but she would like to start the journey as late as possible. What is the latest day she could take the first bus, and still finish her journey by day D?

It is guaranteed that it is possible for Bucket to finish her journey by day D.

## Example
<pre><code><strong>input</strong>: 
3
3 10
3 7 2
4 100
11 10 5 50
1 1
1</code></pre>
<pre><code><strong>output1</strong>:
Case #1: 6
Case #2: 99
Case #3: 1
</code></pre>


## Solution
1. Store the bus days in a stack
2. For each value in the stack, calculate the latest bus day for that bus route 
<blockquote>*** It is important to use <code>long</code> to keep track of the latest day since the last day can be any number up to 10^9.</blockquote>
<pre><code><strong>int busroutes(){
    int tests, size;
    long last;
   cin >> tests;
   for(size_t i = 0; i < tests; ++i){
       cin >> size >> last;
       long ans;
       if(size==1){
           cin >> ans;
           ans = last/ans * ans;
       }else{
           stack&lt;long&gt; list;
           while(--size >= 0){
               long cur;
               cin >> cur;
               list.push(cur);
           }
           while(list.size() > 0){
               long cur = list.top();
               list.pop();
               last = last/cur * cur;
           }
           ans = last;
       }
       
       cout << "Case #" << i+1 << ": " <<  ans << endl;
   }
   return 0;
}</strong></code></pre>
<strong>Time copmlexity: <i>O(t*n)</i></strong>




<!-- <pre><code> -->

