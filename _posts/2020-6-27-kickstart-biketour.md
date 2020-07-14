---
layout: post
category: blog
title:  "Google Kick Start 2020 Round B - Bike Tour"
date:   2020-06-27
tags: algorithm kick_start iteration
image: ""
---

<a href = "https://codingcompetitions.withgoogle.com/kickstart/round/000000000019ffc8/00000000002d82e6">LINK</a>

## Problem
Li has planned a bike tour through the mountains of Switzerland. His tour consists of N checkpoints, numbered from 1 to N in the order he will visit them. The i-th checkpoint has a height of Hi.

A checkpoint is a peak if:
It is not the 1st checkpoint or the N-th checkpoint, and
The height of the checkpoint is strictly greater than the checkpoint immediately before it and the checkpoint immediately after it.

Please help Li find out the number of peaks.

## Example
<pre><code><strong>input1</strong>: 
4
3
10 20 14
4
7 7 7 7
5
10 90 20 90 10
3
10 3 10</code></pre>
<pre><code><strong>output1</strong>:
Case #1: 1
Case #2: 0
Case #3: 2
Case #4: 0
</code></pre>


## Solution
As scanning through the list, keep track of three values: <strong>first, sec, third</strong>. Check if any satisfies the conditions for being a peak.
<pre><code><strong>int biketour(){
    int tests, size;
    cin >> tests;
    for(size_t j = 0; j < tests; ++j){
        cin >> size;
        int bfr, cur, after, count = 0;
        cin >> bfr;
        cin >> cur;
        for(size_t i = 0; i < size-2; ++i){
            cin >> after;
            if(bfr < cur && cur > after){
                    ++count;
            }
            bfr = cur;
            cur = after;
        }
        
        cout << "Case #" << j+1 << ": " << count << endl;
    }
    return 0;
}</strong></code></pre>
<strong>Time copmlexity: <i>O(t*n)</i></strong>




<!-- <pre><code> -->

