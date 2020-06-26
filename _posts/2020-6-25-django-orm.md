---
layout: post
category: blog
title:  "Django - Object Relational Mapper Theory"
date:   2020-06-25
tags: django concepts python
image: ""
---

## ORM
The user uses application to access data. 

Database has tables with data. One object will represent each column.
ex) product table customer table etc.
Customer table wil have cust_id, cust_name, cust_phn data.
<pre><code>classs Customer:
    cust_id: int
    cust_name: str
    cust_phn: int
</code></pre>

<strong>Django</strong> creates a table in database automatically when an object is created in <strong>models.py</strong>, which is called <strong>ORM theory</strong>.

### Database Engine
- Oracle, MySQL, SQLite...
