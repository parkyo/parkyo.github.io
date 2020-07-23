---
layout: post
category: blog
title:  "Bellman Ford algorithm"
date:   2020-07-21
tags: algorithm leetcode greedy
image: ""
---

<strong>Bellman Ford</strong> works like Dijkstra's algorithm except that it also allows negative weights. It is simpler and suites better for the distributed system. 
<br>

### Alogorithm
<pre><code><strong>void BellmanFord(struct Graph* graph, int src) 
{ 
    int V = graph->V; 
    int E = graph->E; 
    int dist[V]; 
    </strong>
    <i>// Step 1: Initialize distances from src to all other vertices 
    // as INFINITE </i><strong>
    for (int i = 0; i < V; i++) 
        dist[i] = INT_MAX; 
    dist[src] = 0; 
    </strong>
    <i>// Step 2: Relax all edges |V| - 1 times. A simple shortest 
    // path from src to any other vertex can have at-most |V| - 1 
    // edges </i><strong>
    for (int i = 1; i <= V - 1; i++) { 
        for (int j = 0; j < E; j++) { 
            int u = graph->edge[j].src; 
            int v = graph->edge[j].dest; 
            int weight = graph->edge[j].weight; 
            if (dist[u] != INT_MAX && dist[u] + weight < dist[v]) 
                dist[v] = dist[u] + weight; 
        } 
    } 
  </strong>
    <i>// Step 3: check for negative-weight cycles.  The above step 
    // guarantees shortest distances if graph doesn't contain 
    // negative weight cycle.  If we get a shorter path, then there 
    // is a negative weight cycle. </i><strong>
    for (int i = 0; i < E; i++) { 
        int u = graph->edge[i].src; 
        int v = graph->edge[i].dest; 
        int weight = graph->edge[i].weight; 
        if (dist[u] != INT_MAX && dist[u] + weight < dist[v]) { 
            printf("Graph contains negative weight cycle"); 
            return; // If negative cycle is detected, simply return 
        } 
    } 
  
    printArr(dist, V); 
  
    return; 
} </strong></code></pre>

<blockquote>O(VE)</blockquote>

<a href="https://www.geeksforgeeks.org/bellman-ford-algorithm-dp-23/">GeeksForGeeks</a>
