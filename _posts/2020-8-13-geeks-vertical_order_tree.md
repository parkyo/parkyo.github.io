---
layout: post
category: blog
title:  "GeeksForGeeks - Vertical Traversal of Tree"
date:   2020-08-13
tags: algorithm must_do geeks important tree bfs
image: ""
---
<a href="https://practice.geeksforgeeks.org/problems/check-for-bst/1">link</a>

## Problem
Traverse the tree verticall from left to right

## Solution 
Use <strong>bfs</strong> and group the nodes in the same vertical axis in order.
<pre><code><strong>void bfs(Node* root, map&lt;int, queue&lt;int&gt;&gt;& mp){
    queue&lt;Node*&gt; q;
    queue&lt;int&gt; axis;
    q.push(root);
    axis.push(0);
    mp[0].push(root->data);
    while(!q.empty()){
        Node* cur = q.front();
        if(cur->left){
            q.push(cur->left);
            int haxis = axis.front() - 1;
            mp[haxis].push((cur->left)->data);
        }
        if(cur->right){
            q.push(cur->right);
            int haxis = axis.front() + 1;
            mp[haxis].push((cur->right)->data);
        }
        
        q.pop();
        axis.pop();
    }
}

vector&lt;vector&lt;int&gt;&gt; verticalOrder(Node* root) {
    map&lt;int, queue&lt;int&gt;&gt; mp;
    bfs(root, mp);
    vector&lt;vector&lt;int&gt;&gt; list(mp.size());

    size_t i = 0;
    for(auto it = mp.begin(); it != mp.end(); ++it){
        list[i].resize((it->second).size());
        size_t j = 0;
        while(!(it->second).empty()){
            list[i][j] = (it->second).front();
            (it->second).pop();
            ++j;
        }
        ++i;
    }
    return list;
}
</strong></code></pre>
<strong>Time Complexity : <i>O(logn)</i></strong>
