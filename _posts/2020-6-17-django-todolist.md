---
layout: post
category: blog
title:  "Django Concepts"
date:   2020-06-17
tags: django concepts python todolist webapp
image: ""
---


<a href = "https://github.com/parkyo/helloworld_webapp"><strong>Helloworld Web App</strong> github</a>


## Make Todo List

<code>python manage.py COMMAND</code> allows you to interact with django project

### Create a new app
<pre><code>$python manage.py startapp {APP_NAME}</code></pre>

### Settings.py
When creating a new app within the project, the app's name has to be added to <code>INSTALLED_APPS</code>

### urls.py
Import new functions <code>from {app_name}.views import {FUNCTION}</code> and add <code>path('{URL}', {FUNCTION})</code>

### models.py
<pre><code>class MODEL_ITEM(models.Model):
    DATA_FIELD = models.TextField()
    DATA_FIELD = models.CharField(max_length = 29)
    ...
</code></pre>

<pre><code>$python manage.py makemigrations
$python manage.py migrate</code></pre>

### views.py
If you created a separate html for the app in templates directory, add <code>from django.shortcuts import render</code>
<strong>django.shortcuts</strong> is a package that collects helper functions and classes that span multiple levels of MVC and introudce control coupling. 
<blockquote><strong>Control coupling</strong> is one module controlling the flow of another by passing it information on what to do. </blockquote> 

<a href = "https://docs.djangoproject.com/en/3.0/topics/http/shortcuts/">reference</a>

<code>render(request, template_name, context=None, content_type=None, using=None)</code> 
<blockquote><strong>render</strong> is gathering data, loading the associated templates, applying the data to the templates, and sending the output to the user. </blockquote>

<code>from django.http import HttpResponse, HttpResposneRedirect</code>
<blockquote><strong>HttpRequest</strong> objects that contain metadata are created automatically by Django</blockquote>
Request and response objects are used to pass state through the system.

<blockquote>Page is requested -> <strong>HttpRequest</strong> created with metadata about the request -> load view with <strong>HttpRequest</strong> -> each returns <strong>HttpResponse</strong> object</blockquote>

<code>return HttpResponse('{url}' or {"{msg}"})</code>

<code>from .models import MODEL_ITEM</code> imports model item from models.py. 
<code>MODEL_ITEM(DATA_FIELD = request.METHOD['INPUT_NAME'])</code>

### settings.py
<pre><code>import os</code></pre>
Add  <code>os.path.join(BASE_DIR, 'templates')</code> in <code>TEMPLATES > DIRS</code> 

In your live server environment, tell WSGI app what settings file to use
<blockquote>WSGI is the Web Server Gateway Interface that forwards requests to web apps or frameworks in Python</blockquote>
<strong>OS module</strong> provides functions for interacting with the operating system. 
<code>os.path.join({a file system path},{path component to be joined})</code> 
<code>BASE_DIR</code> is an absolute path where manage.py lies

### templates > .html
<pre><code>{{todo_item.content}}</pre></code>
