---
layout: post
category: blog
title:  "Leetcode Weekly Contest 197 - Path with Maximum Probability"
date:   2020-07-25
tags: algorithm leetcode weekly_contest DFS
image: ""
---

<a href = "https://leetcode.com/problems/number-of-nodes-in-the-sub-tree-with-the-same-label/">LINK</a>

### Level : Medium

## Problem
Given a tree (i.e. a connected, undirected graph that has no cycles) consisting of n nodes numbered from 0 to n - 1 and exactly n - 1 edges. The root of the tree is the node 0, and each node of the tree has a label which is a lower-case character given in the string labels (i.e. The node with the number i has the label labels[i]).

The edges array is given on the form edges[i] = [ai, bi], which means there is an edge between nodes ai and bi in the tree.

Return an array of size n where ans[i] is the number of nodes in the subtree of the ith node which have the same label as node i.

A subtree of a tree T is the tree consisting of a node in T and all of its descendant nodes.

## Solution
DFS search on tree
<pre><code><strong>class Solution {
public:
    struct Node{
        int val;
        vector&lt;Node*&gt; children;
        Node(int in_val): val(in_val){
        }
    };
    
    void dfs(size_t root, size_t i, vector&lt;Node*&gt;& tree, string& labels, vector&lt;int&gt;& ans){
        if(i < tree.size()){
            for (auto n : tree[i]->children){
                if(labels[n->val] == labels[root]){
                    ++ans[root];
                }
                dfs(root, n->val, tree, labels, ans);
                
            }

        }

    }

    vector&lt;int&gt countSubTrees(int n, vector&lt;vector&lt;int&gt;&gt;& edges, string labels) {
        vector&lt;int&gt; ans(n,1);
        vector&lt;Node*&gt; tree(n);
        for(size_t i = 0; i < n; ++i){
            Node* n = new Node((int)i);
            tree[i] = n;
        }
        for(auto e : edges){
            tree[e[0]]->children.push_back(tree[e[1]]);
        }
        for(size_t i = 0; i < n; ++i){
            dfs(i, i,tree, labels, ans);
        }

        return ans;
    }
};</strong></code></pre>
<strong>Time copmlexity: <i>O(n*E)</i></strong>
