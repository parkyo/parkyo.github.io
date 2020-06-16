---
layout: post
category: blog
title:  "Python vs Python3"
date:   2020-06-14
excerpt: ""
image: "/images/terminal.jpg"
---

<!-- # Python vs Python3 -->
I was confused because when I type <code>python --version</code> in terminal, 
it returned <code>Python 2.7.10</code> but I used <code>python3</code> for django. 
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