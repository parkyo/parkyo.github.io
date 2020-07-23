---
layout: post
category: blog
title:  "Leetcode Weekly Contest 197 - Path with Maximum Probability"
date:   2020-07-19
tags: algorithm leetcode weekly_contest dijkastra
image: ""
---

<a href = "https://leetcode.com/problems/number-of-substrings-with-only-1s/">LINK</a>

### Level : Medium

## Problem
You are given an undirected weighted graph of n nodes (0-indexed), represented by an edge list where edges[i] = [a, b] is an undirected edge connecting the nodes a and b with a probability of success of traversing that edge succProb[i].

Given two nodes start and end, find the path with the maximum probability of success to go from start to end and return its success probability.

If there is no path from start to end, return 0. Your answer will be accepted if it differs from the correct answer by at most 1e-5.

## Solution
BFS search
<pre><code><strong>#include <unordered_map>
#include <queue>
#include <vector>

using namespace std;

class Solution {

    
public:
    
    double maxProbability(int n, vector<vector<int>>& edges, vector<double>& succProb, int start, int end) {
        vector<unordered_map<int, double>> graph(n);
        for(size_t i = 0; i < edges.size(); ++i){
            graph[edges[i][0]][edges[i][1]] =  succProb[i];
            graph[edges[i][1]][edges[i][0]] = succProb[i];
        }
        
        vector<double> ps(n, 0);
        ps[start] = 1.0;
        queue<int> q;
        q.push(start);
        while(!q.empty()){
            int cur = q.front();
            q.pop();
            for (auto it = graph[cur].begin(); it != graph[cur].end(); ++it){
                double pos = (it->second) * ps[cur];
                if(pos > ps[it->first]){
                    ps[it->first] = pos;
                    q.push(it->first);
                }
            }

        }
        return ps[end];
        
    }
};</strong></code></pre>
<strong>Time copmlexity: <i>O(V*E)</i></strong>





