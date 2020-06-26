---
layout: post
category: blog
title:  "HTTP Methods - GET vs POST"
date:   2020-06-25
tags: django concepts python HTTP
image: ""
---
<a href = "https://www.youtube.com/watch?v=OTmQOjsl0eg"> recommendation for Django tutorial</a>

## HTTP Protocol
<span class = "image fit"><img src = "/images/httpprotocol.png"/></span>

<strong>Request Methods</strong> GET POST PUT DELETE HEAD CONNECT OPTION TRACE PATCH

### GET
: fetch data from the server
The data is sent to the address bar. So we don't want to use <code>GET</code> for private data such as userID and password

### POST
: update data of the server
Use <code>CSRF Token</code> for this method