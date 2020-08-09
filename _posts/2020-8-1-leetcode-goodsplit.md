---
layout: post
category: blog
title:  "Leetcode Bi-Weekly Contest 31 - Good ways to split a string"
date:   2020-07-25
tags: algorithm leetcode weekly_contest DFS
image: ""
---

<a href = "https://leetcode.com/problems/number-of-good-ways-to-split-a-string/submissions/">LINK</a>

### Level : Medium

## Problem
You are given a string s, a split is called good if you can split s into 2 non-empty strings p and q where its concatenation is equal to s and the number of distinct letters in p and q are the same.

Return the number of good splits you can make in s.

## Solution
<a href="/sliding-window/">Sliding Window Technique</a>
<pre><code><strong>int numSplits(string s) {
        vector&lt;vector&lt;int&gt;&gt; chars(s.size()-1, vector&lt;int&gt; (2,0));
        int count = 0;
        unordered_set&lt;char&gt; s1;
        unordered_set&lt;char&gt; s2;
        size_t i = 0, j = chars.size() -1;
        while(i < chars.size() && j >= 0){
            s1.insert(s[i]);
            s2.insert(s[j+1]);
            chars[i][0] = (int)s1.size();
            chars[j][1] = (int)s2.size();
            ++i;
            --j;
        }
        for(auto i : chars){
            if(i[0] == i[1]){
                ++count;
            }
        }
        return count;
    }
};</strong></code></pre>
<strong>Time copmlexity: <i>O(n)w</i></strong>
