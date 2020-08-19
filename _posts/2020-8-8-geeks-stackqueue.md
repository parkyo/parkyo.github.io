---
layout: post
category: blog
title:  "GeeksForGeeks - Queue using two stacks"
date:   2020-08-08
tags: algorithm must_do stack queue geeks
image: ""
---
<a href="https://practice.geeksforgeeks.org/problems/queue-using-two-stacks/1>link</a>

## Problem
Implement a Queue using 2 stacks s1 and s2 .
A Query Q is of 2 Types
1. 1 x (a query of this type means  pushing 'x' into the queue)
2. 2   (a query of this type means to pop element from queue and print the poped element)
## Solution
<pre><code><strong>class StackQueue{
private:
    stack<int> s1;
    stack<int> s2;
    
public:
    void push(int v){
        s1.push(v);
    }
    
    int pop(){
        if(s1.empty()){
            return -1;
        }
        while(s1.size() > 1){
            s2.push(s1.top());
            s1.pop();
        }
        int rem = s1.top();
        s1.pop();
        while(!s2.empty()){
            s1.push(s2.top());
            s2.pop();
        }
        return rem;
    }
};
</strong></code></pre>
