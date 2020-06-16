---
layout: post
category: blog
title:  "Convert a snake case to a camel case"
date:   2020-06-16
excerpt: ""
image: ""
---

## Problem
Convert from snake-case to camel-case and return it.

## Example
<pre><code><strong>input</strong>: 
naver_webtoon
NAVER_WEBTOON
</code></pre>
<pre><code><strong>output</strong>:
naverWebtoon
naverWebtoon</code></pre>

<blockquote> written in C++</blockquote>

## Solution 1
1. loop through the snake case string
2. As iterationg, have a boolean 'cap' and update it if there is a underdash to convert the next letter to cap
<br><strong>Time Complexity = <i>O(n)</i></strong>

<pre><code>
<strong>
string convertCamel(string snake){
    string camel;
    bool cap = false;
    for(char c : snake){
        if(!cap && (int)c < 91){</strong><i>//if the char is cap when it shouldn't be</i><strong>
            camel.push_back(tolower(c)); 
        }else if(c == '_'){</strong><i>//if there is an underdash, the next char should be capitalized</i><strong>
            cap = true;
        }else if(cap){</strong><i>//if there should be a cap char convert the char to cap if it is not. Else, just push it back</i><strong>
            if((int)c > 97){
                camel.push_back(toupper(c));
            }else{
                camel.push_back(c);
            }
            cap = false;
        }else{
            camel.push_back(c);
        }
    }
    return camel;
}   
</strong>
</code></pre>