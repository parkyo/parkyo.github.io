---
layout: post
category: blog
title:  "Check if a string is a substring of another"
date:   2020-06-16
excerpt: ""
image: ""
---

## Problem
Check if a string is a substring of another string. If true, return the index of the substring's first letter in another string. Else, return -1.
<br>
After research, I realized that mutliple versions of Python can be installed and exist simultaneously.
And the symbolic link for python on my computer was directed to <code>Python 2.7.10</code>, which is why when I had to type <code>python3</code> instead of <code>python</code> in order to use the latest Python. 
So I installed newest python by Homebrew
<pre><code>
brew install python
</code></pre> 
set symlink from python to python3
<pre><code>
ls -l -f /usr/local/bin/python3 /usr/local/bin/python
</code></pre> 
assigned the command 'python' to 'python3'
<pre><code>
alias python=python3
</code></pre> 