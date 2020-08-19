---
layout: post
category: blog
title:  "Leetcode - Populating Next Right Pointers in Each Node"
date:   2020-08-14
tags: algorithm leetcode tree 
image: ""
---
<a href="https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/">link</a>

## Problem
You are given a perfect binary tree where all leaves are on the same level, and every parent has two children. 
Populate each next pointer to point to its next right node. If there is no next right node, the next pointer should be set to NULL.

Initially, all next pointers are set to NULL.

## Solution 
I initially had,
<pre><code><strong>Node* connect(Node* root) {
        Node* arr[4096];
        Node* cur = root;
        size_t i = 1;
        arr[i-1] = root;
        if(root){
            int level = 2;
            int count = 1;
            while(arr[i-1]->left){
                arr[i*2-1] = arr[i-1]->left;
                arr[i*2] = arr[i-1]->right;
                count += 2;
                arr[i*2-1]->next = arr[i*2];
                if(count < pow(2, level)-1){
                    arr[i*2]->next = arr[i]->left;
                }else{
                    ++level;
                }
                ++i;
            }
        }
        
        return arr[0];
    }
</strong></code></pre>
<strong>Time Complexity : <i>O(n)</i></strong>
<br>
However, I optimized the space to O(1) by removing the vector since you can traverse with previously connected nodes
<pre><code><strong> Node* connect(Node* root) {
        size_t i = 1;
        if(!root){
            return root;
        }
        Node* first = root;
        while(first->left){
            Node* cur = first;
            while(cur){
            (cur->left)->next = cur->right;
            if(cur->next){
                (cur->right)->next = (cur->next)->left;
            }
            cur = cur->next;
            }
            first = first->left;
        }
        
        return root;
    }</strong></code></pre>