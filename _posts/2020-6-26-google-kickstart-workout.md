---
layout: post
category: blog
title:  "Google Kick Start 2020 Round A - Workout"
date:   2020-06-26
tags: algorithm kick_start
image: ""
---

<a href = "https://codingcompetitions.withgoogle.com/kickstart/round/000000000019ffc7/00000000001d3f5b">LINK</a>

## Problem
Tambourine has prepared a fitness program so that she can become more fit! The program is made of N sessions. During the i-th session, Tambourine will exercise for Mi minutes. The number of minutes she exercises in each session are strictly increasing.

The difficulty of her fitness program is equal to the maximum difference in the number of minutes between any two consecutive training sessions.

To make her program less difficult, Tambourine has decided to add up to K additional training sessions to her fitness program. She can add these sessions anywhere in her fitness program, and exercise any positive integer number of minutes in each of them. After the additional training session are added, the number of minutes she exercises in each session must still be strictly increasing. What is the minimum difficulty possible?

## Example
<pre><code><strong>input1</strong>: 
1
3 1
100 200 230</code></pre>
<pre><code><strong>output1</strong>:
Case #1: 50
</code></pre>

<pre><code><strong>input2</strong>: 
3
5 2
10 13 15 16 17
5 6
9 10 20 26 30
8 3
1 2 3 4 5 6 7 10</code></pre>
<pre><code><strong>output</strong>:
Case #1: 2
Case #2: 3
Case #3: 1
</code></pre>

## Solution 1 
<p>

<strong>Time copmlexity: <i>O(log(max_diff)*n)</i></strong></p>
<span class="image left"><img width="50%" src="/images/workout.png"/></span>



<!-- <pre><code> -->

