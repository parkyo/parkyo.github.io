---
layout: post
category: blog
title:  "Django Concepts for TODO List"
date:   2020-06-17
tags: django concepts python
image: ""
---
<a href = "https://github.com/parkyo/helloworld_webapp"><strong>Helloworld Web App</strong> github</a>


## Make Todo List

<code>python manage.py COMMAND</code> allows you to interact with django project

### Settings.py
When creating a new app within the project, the app's name has to be added to <code>INSTALLED_APPS</code>

### urls.py
Import new functions from {app_name}.views and add <code>path('{url}', {function})</code>

### views.py
If you created a separate html for the app in templates directory, add <code>from django.shortcuts import render</code>
<strong>django.shortcuts</strong> is a package that collects helper functions and classes that span multiple levels of MVC and introudce control coupling. 
<blockquote><strong>Control coupling</strong> is one module controlling the flow of another by passing it information on what to do. </blockquote> 

<a href = "https://docs.djangoproject.com/en/3.0/topics/http/shortcuts/">reference</a>


<code>render(request, template_name, context=None, content_type=None, using=None)</code> 
<blockquote><strong>render</strong> is gathering data, loading the associated templates, applying the data to the templates, and sending the output to the user. 

#### required
<strong>request </strong>: object used to generate this response
<strong>template_name</strong>

#### optional
<strong>context </strong>: a dictionary of values to add to the template context
<strong>content_type </strong>: the MIME type to use fo rthe resulting doc.
<blockquote><strong>MIME types</strong>: is a media type that describes the nature and format of a document, file or assortment of bytes. <code>type/subtype</code></blockquote>
<strong>status</strong>: status code for the response
<strong>using</strong> : the name of a template engine to use for loading the template

<code>from django.http import HttpResponse, HttpResposneRedirect</code>
<blockquote><strong>HttpRequest</strong> objects that contain metadata are created automatically by Django</blockquote>
Request and response objects are used to pass state through the system.

<blockquote>Page is requested -> <strong>HttpRequest</strong> created with metadata about the request -> load view with <strong>HttpRequest</strong> -> each returns <strong>HttpResponse</strong> object</blockquote>

<code>return HttpResponse('{url}' or {"{msg}"})</code>

### settings.py
<pre><code>import os</code></pre>
Add  <code>os.path.join(BASE_DIR, 'templates')</code> in <code>TEMPLATES > DIRS</code> 

In your live server environment, tell WSGI app what settings file to use
<blockquote>WSGI is the Web Server Gateway Interface that forwards requests to web apps or frameworks in Python</blockquote>
<strong>OS module</strong> provides functions for interacting with the operating system. 
<code>os.path.join({a file system path},{path component to be joined})</code> 
<code>BASE_DIR</code> is an absolute path where manage.py lies
