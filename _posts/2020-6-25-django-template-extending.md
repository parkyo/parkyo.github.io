---
layout: post
category: blog
title:  "Django - template extending"
date:   2020-06-25
tags: django concepts python
image: ""
---

<strong>Template extending</strong> means you can reuse same parts of HTML for different pages of website and prevent you from code repetition.

### How To
<ol>
<li>Create a base template <code>templates/base.html</code></li>
<span class = "image fit"><img src = "/images/basehtml.png"/></span>

<li>Replace the part which content is dependent on other templates with <code>&#123;&#37; block content &#37;&#125;&#123;&#37; endblock &#37;&#125;</code></li>
<span class = "image fit"><img src = "/images/basehtml2.png"/></span>

<li>In other templates, extend <code>base.html</code> and code what should be inside of <code>&#123;&#37; block content &#37;&#125;&#123;&#37; endblock &#37;&#125;</code></li>
<span class = "image fit"><img src = "/images/extendhtml.png"/></span>
</ol>

