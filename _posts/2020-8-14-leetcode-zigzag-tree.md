---
layout: post
category: blog
title:  "Leetcode - Binary Tree Zig Zag Level Order Traversal"
date:   2020-08-14
tags: algorithm leetcode tree BTS important
image: ""
---
<a href="https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/">link</a>

## Problem
Traverse the tree verticall from left to right

## Solution 
Level order traversal with two stacks. 
Second stack should store the children reversely (right and left)
<pre><code><strong>vector&lt;vector&lt;int&gt;&gt; zigzagLevelOrder(TreeNode* root) {
        vector&lt;vector&lt;int&gt;&gt; list;
        if(root){
            stack&lt;TreeNode*&gt; s1;
            stack&lt;TreeNode*&gt; s2;
            s1.push(root);
            while(!s1.empty() || !s2.empty()){
                if(!s1.empty()){
                    list.resize(list.size() + 1);
                }
                while(!s1.empty()){
                    TreeNode* cur = s1.top();
                    s1.pop();
                    if(cur->left){
                        s2.push(cur->left);
                    }
                    if(cur->right){
                        s2.push(cur->right);
                    }
                    list[list.size()-1].push_back(cur->val);
                }
                if(!s2.empty()){
                    list.resize(list.size()+1);
                }
                while(!s2.empty()){
                    TreeNode* cur = s2.top();
                    s2.pop();
                    if(cur->right){
                        s1.push(cur->right);
                    }
                    if(cur->left){
                        s1.push(cur->left);
                    }
                    list[list.size()-1].push_back(cur->val);
                }
            }
        }
        
        return list;
    }
</strong></code></pre>
<strong>Time Complexity : <i>O(n)</i></strong>
