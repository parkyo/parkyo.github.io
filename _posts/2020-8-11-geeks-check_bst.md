---
layout: post
category: blog
title:  "GeeksForGeeks - Check if the tree is a binary search tree"
date:   2020-08-11
tags: algorithm must_do geeks tree recursion important
image: ""
---
<a href="https://practice.geeksforgeeks.org/problems/check-for-bst/1">link</a>

## Problem
Given a binary tree. Check whether it is a BST or not.

## Solution 
Use recursioin by setting the low and high points 

<pre><code><strong>bool helper(Node* root, Node* low, Node* high){
    if(!root){ </strong><i>//ALWAYS base case for tree recursion</i><strong>
        return true;
    }
    if(low && low->data >= root->data){</strong><i>// Base 2 - !low can mean it is left-side node</i><strong>
        return false;
    }
    if(high && high->data <= root->data){
        return false;
    }
    return helper(root->left, low, root) && helper(root->right, root, high);
     </strong><i>// BOTH should be true therefore use &&
     // doesn't need to change low if it moves to the left side (vice versa)</i><strong>
}

bool isBST(Node* root) {
    helper(root, NULL, NULL);
}
</strong></code></pre>
<strong>Time Complexity : <i>O(logn)</i></strong>
