---
layout: post
category: blog
title:  "Google Kick Start 2020 Round A - Allocation"
date:   2020-06-19
excerpt: ""
image: ""
---

<a href = "https://codingcompetitions.withgoogle.com/kickstart/round/000000000019ffc7/00000000001d3f56">LINK</a>

## Problem
There are N houses for sale. The i-th house costs Ai dollars to buy. You have a budget of B dollars to spend.
What is the maximum number of houses you can buy?

## Example
<pre><code><strong>input</strong>: 
3
4 100
20 90 40 90
4 50
30 30 10 10
3 300
999 999 999</code></pre>
<pre><code><strong>output</strong>:
Case #1: 2
Case #2: 3
Case #3: 0</code></pre>

<blockquote> written in C++</blockquote>

First of all, I read the word 'maximum' in the problem and automatically thought it was an optimization problem with dynamic programming. I tried to solve it with dp but NOPE lol. It was a simple problem.

## Solution
Sort the prices in the ascending order. Increment the count as looping through and adding the prices to the total price until the total prices go over the given amount of dollars. 


<pre><code>
<strong>int main(){
    int tests, size, b;
    cin >> tests;
    while(--tests >= 0){
        cin >> size >> b;
        int cur;
        vector &lt;int&gt; prices(size);
        for(size_t i = 0; i < prices.size(); ++i){
            cin >> cur;
            prices[i] = cur;
        }
        int cur_total = 0;
        int count = 0;
        sort(prices.begin(), prices.end());
        for(size_t i = 0; i < prices.size(); ++i){
            if (cur_total + prices[i] <= b){
                ++count;
                cur_total += prices[i];
            }
        }
        cout << count;
    }
    return 0;
    
}   </strong>
</code></pre>

<strong>Time Complexity = <i>O(nlogn)</i></strong>

<blockquote>Think about greedy algorithm first</blockquote>