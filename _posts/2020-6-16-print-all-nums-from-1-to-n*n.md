---
layout: post
category: blog
title:  "Print all numbers from 1 to n*n"
date:   2020-06-16
excerpt: ""
image: ""
---

## Problem
Print all numbers from 1 to n^2 in 'ㄹ' shape

## Example
<pre><code><strong>input</strong>: 
4
5
</code></pre>
<pre><code><strong>output</strong>:
1 2 3 4
8 7 6 5 
9 10 11 12
16 15 14 13

1 2 3 4 5
10 9 8 7 6
11 12 13 14 15
20 19 18 17 16
21 22 23 24 25</code></pre>

<blockquote> written in C++</blockquote>

## Solution 1
Use <code>std::stack</code> to store every even number line
<br><strong>Time Complexity = <i>O(n)</i></strong>

<pre><code>
<strong>
void printMultiples(int n){
    stack<int> reverseList;
    size_t line = 1;
    for(size_t i = 1; i <= n*n; ++i){
        if (line %2 == 0){
            reverseList.push((int)i);
        }else{
            cout << i << " ";
        }
        if (i%n == 0 && line %2 == 1){
            ++line;
            cout << "\n";
        }
        if (reverseList.size() == n){
            for(size_t j = 0; j < n; ++j){
                cout << reverseList.top() << " ";
                reverseList.pop();
            }
            cout << "\n";
        }
    }
}
</strong>
</code></pre>