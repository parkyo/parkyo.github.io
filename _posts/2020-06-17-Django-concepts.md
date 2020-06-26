---
layout: post
category: blog
title:  "Django Concepts"
date:   2020-06-25
tags: django concepts python
image: ""
---

### Django
MVT - Model View Template

To accomplish <strong>Separation of Concern</strong> by separating...
<li>Data - Model</li>
<li>Layout - Django Template Language allows dynamic data</li>
<li>Logic</li>

<span class="image fit"><img src="/images/MVT.png"/></span>
Data from database is linked with <strong>Model</strong>. <strong>View</strong> links <strong>Model</strong> and <strong>Template</strong> together. When the user sends a request, it goes to the framework forming a URL that navigates to <strong>View</strong>. In <strong>View</strong>, we write busienss logic. Then, it will use the model and template objects to decide what data to be sent on <strong>template </strong>from <strong>model</strong>.

### MVT vs. MVC
<li>Model = Model</li>
<li>Template = View</li>
<li>View = Controller</li>

However, MVC needs a configuration for <strong>Controller</strong> where as <strong>Django</strong> does it automatically. 

### Advantages
<li>Develop Fast</li>
<li>Provide Bundled Components </li>
<li>Data Security </li>
<li>Scalability </li>

