---
layout: post
category: blog
title:  "Google Kick Start 2020 Round D - Record Breaker"
date:   2020-07-14
tags: algorithm kick_start iteration
image: ""
---

<a href = "https://codingcompetitions.withgoogle.com/kickstart/round/000000000019ff08/0000000000387171">LINK</a>

### Level : Easy

## Problem
Isyana is given the number of visitors at her local theme park on N consecutive days. The number of visitors on the i-th day is Vi. A day is record breaking if it satisfies both of the following conditions:
- The number of visitors on the day is strictly larger than the number of visitors on each of the previous days.
- Either it is the last day, or the number of visitors on the day is strictly larger than the number of visitors on the following day.
Note that the very first day could be a record breaking day!

Please help Isyana find out the number of record breaking days.

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
Case #1: 2
Case #2: 1
Case #3: 3
Case #4: 0
</code></pre>


## Solution
Know how to use indices
<pre><code><strong>int main(){
    int tests;
    cin >> tests;
    for(size_t i = 0; i < tests; ++i){
        int num;
        cin >> num;
        vector<int> list(num);
        for(size_t j = 0; j < num; ++j){
            int cur;
            cin >> cur;
            list[j] = cur;
        }
        int max = -1;
        int count = 0;
        for(size_t j = 0; j < num; ++j){
            if(list[j] > max){
                max = list[j];
                if(j == list.size()-1||list[j+1]< list[j]){
                    ++count;
                }
            }
        }
        

        cout << "Case #" << i+1 << ": " << count  << endl;
    }
    return 0;
}</strong></code></pre>
<strong>Time copmlexity: <i>O(t*n)</i></strong>




<!-- <pre><code> -->

