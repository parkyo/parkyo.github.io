---
layout: post
category: blog
title:  "Google Kick Start 2020 Round A - Workout"
date:   2020-06-24
tags: algorithm kick_start
image: ""
---

<a href = "https://codingcompetitions.withgoogle.com/kickstart/round/000000000019ffc7/00000000001d3ff3">LINK</a>

## Problem
Pip has N strings. Each string consists only of letters from A to Z. Pip would like to bundle their strings into groups of size K. Each string must belong to exactly one group.

The score of a group is equal to the length of the longest prefix shared by all the strings in that group. For example:
The group {RAINBOW, RANK, RANDOM, RANK} has a score of 2 (the longest prefix is 'RA').
The group {FIRE, FIREBALL, FIREFIGHTER} has a score of 4 (the longest prefix is 'FIRE').
The group {ALLOCATION, PLATE, WORKOUT, BUNDLING} has a score of 0 (the longest prefix is '').

Please help Pip bundle their strings into groups of size K, such that the sum of scores of the groups is maximized.

## Example
<pre><code><strong>input</strong>: 
2
2 2
KICK
START
8 2
G
G
GO
GO
GOO
GOO
GOOO
GOOO</code></pre>
<pre><code><strong>output</strong>:
Case #1: 0
Case #2: 10
</code></pre>


## Solution 1 
<blockquote>(MLT for bigger test set)</blockquote>
(explanation to come..)


<pre><code>
<strong>
int main(){
    int tests, size, b;
    cin >> tests;
    for(size_t j = 0; j < tests; ++j){
        int score = 0;
        cin >> size >> b;
        unordered_map&lt;string, int&gt; list;
        for(size_t i = 0; i < size; ++i){
            string w;
            cin >> w;
            string cur = "";
            for(size_t k =0; k < w.size(); ++k){
                cur.push_back(w[k]);
                auto it = list.find(cur);
                if(it == list.end()){
                    list.insert(pair&lt;string,int&gt;(cur, 1));
                }else{
                    ++(it->second);
                }
            }
            
            
        }
        for(auto it = list.begin(); it != list.end(); ++it){
            score += ((it->second)/b);
        }
        
        cout << "Case #" << j+1 << ": " << score << endl;
    }
    return 0;
}
   </strong>
</code></pre>

### Solution 2
Use <strong>trie</strong>

<!-- <pre><code> -->

