---
layout: post
category: blog
title:  "Prim vs. Djikstra"
date:   2020-07-17
tags: algorithm leetcode greedy
image: ""
---

<strong>Prim's algorithm</strong> is for finding Minimum Spanning Tree that connects ALL vertices of an undirected weighted graph with the lowest possible sum of its edge weights.
<ul>
<li>only work on undirected graph</li>
<li>can handle negative weights</li></ul>
<br>
<strong>Djikstra's algorithm</strong> is a greedy algorithm for finding the shortest path between two vertices with the lowest possibel sum of edge weights
<ul>
<li>can work on both directed and undirected graphs</li>
<li>cannot handle negative weights</li>
<li>O(VlogV)</li></ul>
<br>
