---
layout: post
category: blog
title:  "GeeksForGeeks - Intersection Point in Y Shaped Linked List"
date:   2020-08-08
tags: algorithm must_do LinkedList important geeks
image: ""
---
<a href="https://practice.geeksforgeeks.org/problems/intersection-point-in-y-shapped-linked-lists/1/">link</a>

## Problem
Given two singly linked lists of size N and M, write a program to get the point where two linked lists intersect each other.

## Solution1
My initial thought was to iterate through two lists to figure out the size difference.
Then, I can set the starting point for the longer Linked List and iterate through both to see if the data of the current nodes are the same.
<pre><code><strong>int intersectPoint(Node* head1, Node* head2)
{
    int diff = -1, ans = 0;
    Node* n1 = head1;
    Node* n2 = head2;
    Node* longer = head1;
    Node* shorter = head2;
    while(n1 && n2){
        n1 = n1->next;
        n2 = n2->next;
        ++diff;
    }
    if(n2){
        longer = head2;
        shorter = head1;
    }
    if(!n1 && !n2){
        diff = 0;
    }
    while(diff > 0){
        longer = longer->next;
        --diff;
    }
    while(longer){
        if(longer->data == shorter->data){
            ans = longer->data;
        }else{
            ans = -1;
        }
        longer = longer->next;
        shorter = shorter->next;
    }
    return ans;
}

</strong></code></pre>
<strong>Time Complexity : <i>O(n+m)</i></strong>

## Solution 2
<strong>*** Much better solution</strong>
Iterate through either list and multiply -1 to all nodes.
Then iterate through the other list and any negative number you encounter is the intersection. <i>(fcking brilliant)</i>
<pre><code><strong>int intersectPoint(Node* head1, Node* head2)
{
    int ans = -1;
    while(head1){
        head1->data *= -1;
        head1 = head1->next;
    }
    while(head2){
        if(head2->data < 0){
            ans = head2->data;
        }
        head2 = head2->next;
    }
    return ans;
</strong></code></pre>

### How to approach this solution
Consider that the intersection is not only when the data are the same but the <strong>addresses</strong> are the same. So if the intersected node's data changes, the other list will change as well. Also, always try to use all the <strong>conditions</strong> given as advantages: all node values are positive. We could've changed the node values as 0 or any negative number that the default value can't be. 