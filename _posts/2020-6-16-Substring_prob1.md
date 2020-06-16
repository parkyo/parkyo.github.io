---
layout: post
category: blog
title:  "Check if a string is a substring of another"
date:   2020-06-16
excerpt: ""
image: ""
---

## Problem
Check if a string is a substring of another string. If true, return the index of the substring's first letter in the other string. Else, return -1.

## Example
<pre><code><strong>input</strong>: 
abcde cd
abcde cda
abcd de
abcbcde bc</code></pre>
<pre><code><strong>output</strong>:
2
-1
-1
1</code></pre>

<blockquote> written in C++</blockquote>

## Solution 1
1. loop through the string <strong>a</strong>
2. As iterating, check if the current char matches any char of the string <strong>b</strong>.
3. If they do, iterate through the string <strong>b</strong> along with a to check if all the chars match
<br><strong>Time Complexity = <i>O(n)</i></strong>

<pre><code>
<strong>int substring(string a, string b){
    int result = -1; //result to return
    size_t b_ind = 0; //index to iterate through b
    for(size_t i = 0; i < a.size(); ++i){
        if(b[b_ind] == a[i]){ </strong><i>//if the first char of b matches the char in a</i><strong>
        if (b_ind == 0){ </strong><i>//if it is the first letter in b, save it in result</i><strong>
                result = (int)i;
            }
            if (b_ind == b.size() -1){</strong><i>//if all chars in b are in a, return result</i><strong>
                return result;
            }
            ++b_ind;</strong><i>//update b_ind to iterate</i><strong>
        }else if (b_ind > 0 && a[i-1] == a[i]){ </strong><i>//if b_ind is at 1 and prev char in a equals to the current, cout it as found </i><strong>
            if (b_ind == 1){                       
                ++result;
            }
        }else{ </strong><i>//if the chars don't match, reset result and b_ind</i><strong>
            if (result != -1){
                result = -1;
            }
            b_ind = 0;
        }

    }

    if (b_ind != b.size()){
        result = -1;
    }
    return result;
}   </strong>
</code></pre>

## Solution 2
Use <a href = "http://www.cplusplus.com/reference/string/string/find/"><code>std::string find(string str)</code></a> 


<pre><code><strong>
int substring(string a, string b){
    size_t found = a.find(b);
    if (found == a.npos){
        return -1;
    }else{
        return found;
    }
}
</strong></code></pre>
<strong>Time Complexity = <i>O(n)</i></strong>

## Follow-up
What if the string a contains multiple words with space in between and b is a word? 
### Example
<pre><code><strong>input</strong>: 
"geeks for geeks" "for"
"geeks for geeks" "sfor"</code></pre>
<pre><code><strong>output</strong>:
6
-1</code></pre>

Solution is the same with <strong>Solution 2</strong>. 