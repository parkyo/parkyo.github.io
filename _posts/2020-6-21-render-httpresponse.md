---
layout: post
category: blog
title:  "render vs. HTTPResponse vs. HTTPResponseredirect"
date:   2020-06-21
tags: concepts web server-side django
---
<p>
<strong>HTTP reponse code</strong> indicates a specific HTTP request has been successfully completed
<ol>
<li>Informatioin responses(100-)</li>
<li>Successful responses (200-)</li>
<li>Redirects (300-)</li>
<li>Client errors (400-)</li>
<li>Server errors (400-)</li>
</ol>
</p>
<p>
<code><strong>200 OK</strong></code>
<li><strong>GET</strong>: fetching and transmission of the source in the message body</li>
<li><strong>HEAD</strong>: the entity headers are in the message body</li>
<li><strong>PUT or POST</strong>: transmission of the resource describing the result in the message body</li>
<li><strong>TRACE</strong>: the request message in the message body as received by the server</li>
</p>

### HTTPResponse()
<blockquote>HTTP 200</blockquote>
<li>returns a HTTPResponse object</li>
<li>usually used for small responses such as ajax dadta or small numbers</li>
<br>

### HTTPResponseredirect()
<blockquote>HTTP 302 (found/moved temporarily)</blockquote>
<li>redirects the page to the given url parameter</li>
<br>

### Render(request, template_name, context=None, content_type=None, stats-None, using=None)
<li>instead of rendering the template in HTTPResponse()</li>
<li>combines the template with the context and returns HTTPResponse object</li><br>

#### required
<strong>request </strong>: object used to generate this response
<strong>template_name</strong>

#### optional
<strong>context </strong>: a dictionary of values to add to the template context
<strong>content_type </strong>: the MIME type to use fo rthe resulting doc.
<blockquote><strong>MIME types</strong>: is a media type that describes the nature and format of a document, file or assortment of bytes. <code>type/subtype</code></blockquote>
<strong>status</strong>: status code for the response
<strong>using</strong> : the name of a template engine to use for loading the template

### Redirect(to, args, permanent=false, kwargs)
<li>instead of calling reverse within HTTPResponseredirect(), call redirect to move to the given url</li>
<li>cannot transfer data between pages</li>
<li>use names from url pattern in urls.py</li>