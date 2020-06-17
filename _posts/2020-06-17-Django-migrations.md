---
layout: post
category: blog
title:  "Django Migrations"
date:   2020-06-14
excerpt: ""
image: "/images/django_migrations.jpg"
---

<a href = "https://realpython.com/django-migrations-a-primer/"> reference</a>

<strong>Django</strong> is designed to work with a relational database managed in MySQL, SQLite.
<strong>A relational database</strong> organizes data in table composed of a fixed numbe of cols and infinite number of rows. Each column has a specific data type. A database schema describes these tables with their columns and datatypes. 
Instead of working directly with SQL, Django provides an object-relational mapper which maps the relational database to the wrld of OOP. You write Django models in python that define database fields that correspond to the cols in their database tables. When you update your models, migrations in teh app update the database tables. 
With <strong>django Migrations</strong>, you can easily keep multiple instances of databases in sync with your models. 

<code>makemigrations</code> create individual migration files based on the changes in models
<code>migrate</code> apply and unapply those migrations made to database
<code>sqlmigrate</code> displays the SQL statements for a migration
<code>showmigrations</code> lists a project's migrations and their status

### models.py
<span class = "image center"><img src = "/images/helloworld_models.png"/></span>

### migrate.py
<span class = "image center"><img src = "/images/helloworld_migrate.png"/></span>

