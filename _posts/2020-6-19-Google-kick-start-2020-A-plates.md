---
layout: post
category: blog
title:  "Google Kick Start 2020 Round A - Plates"
date:   2020-06-19
tags: algorithm kick_start dp bottom_up 
image: ""
---

<a href = "https://codingcompetitions.withgoogle.com/kickstart/round/000000000019ffc7/00000000001d40bb">LINK</a>

## Problem
Dr. Patel has N stacks of plates. Each stack contains K plates. Each plate has a positive beauty value, describing how beautiful it looks.

Dr. Patel would like to take exactly P plates to use for dinner tonight. If he would like to take a plate in a stack, he must also take all of the plates above it in that stack as well.

Help Dr. Patel pick the P plates that would maximize the total sum of beauty values.

## Example
<pre><code><strong>input</strong>: 
2
2 4 5
10 10 100 30
80 50 10 50
3 2 3
80 80
15 50
20 10</code></pre>
<pre><code><strong>output</strong>:
Case #1: 250
Case #2: 180</code></pre>

<blockquote>I have realized a lot of my test failures come from small errors like not checking enough conditions or confusing variables.
These small mistakes always prevent me from getting scores even after making almost perfect solution.
I think this comes from experience to detect what common errors can be in the solution or what specific formants are necessary for each competition.</blockquote>

## Solution
Similar to <strong>0/1 Knapsack Problem</strong> Bottom-up Approach
1. Make two vectors to store values of all plates and to keep track of dynamic programming.
2. When storing values, store accumulated values per stack
3. dp[i][j] = max(dp[i-1][j-n] + values[i][n] where n from 0 to k)


<pre><code>
<strong>
int main(){
    int tests, s, p, num;
    cin >> tests;
    for(size_t i = 0; i < tests; ++i){
        cin >> s >> p >> num;
        vector&lt;vector&lt;int&gt;&gt; stacks(s, vector&lt;int&gt;(p+1));
        vector&lt;vector&lt;int&gt;&gt; sol(s, vector<&lt;ntgt;(num+1));
        int cur = 0;
        for(size_t j = 0; j < s; ++j){
            for(size_t k = 1; k < p+1; ++k){
                cin >> cur;
                stacks[j][k] = stacks[j][k-1] + cur;
            }
        }
        
        for(size_t j = 0; j < s; ++j){
            for(size_t k = 1; k < num+1; ++k){
                if(j == 0){
                    if(k > p){
                        sol[j][k] = sol[j][k-1];
                    }else{
                        sol[j][k] = stacks[0][k];
                    }
                }else{
                    int max = 0;
                    for(size_t n = 0; n <= k; ++n){
                        int part = sol[j-1][k-n];
                        if(n <= p){
                            part += stacks[j][n];
                        }else{
                            part += stacks[j][p];
                        }
                            if(max < part){
                                max = part;
                            }
                    }
                    sol[j][k] = max;
                }
                
            }
        }
        
        cout << "Case #" << i+1 << ": " << sol[s-1][num] << endl;
    }
    return 0;
    
}
   </strong>
</code></pre>

<strong>Time Complexity = <i>O(s*p*num)</i></strong>

