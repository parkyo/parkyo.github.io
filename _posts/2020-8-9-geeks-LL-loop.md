---
layout: post
category: blog
title:  "GeeksForGeeks - Detect Loop in Linked List"
date:   2020-08-09
tags: algorithm must_do LinkedList geeks
image: ""
---
<a href="https://practice.geeksforgeeks.org/problems/detect-loop-in-linked-list/1">link</a>

## Problem
Given a linked list of N nodes. The task is to check if the the linked list has a loop. Linked list can contain self loop.

## Solution
<pre><code><strong>struct Node
{
    int data;
    struct Node *next;
    Node(int x) {
        data = x;
        next = NULL;
    }


bool detectLoop(Node* head)
{
    // your code here
    while(head){
        if(head->data < 0){
            return true;
        }
        head->data *= -1;
        head = head->next;
    }
    return false;
}

</strong></code></pre>
<strong>Time Complexity : <i>O(n)</i></strong>