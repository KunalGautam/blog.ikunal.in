---
id: 129
title: "Understanding Directory Structure"
date: "2019-07-15T14:34:19+05:30"
author: "Kunal Gautam"
layout: post

url: /kunal/2019/07/15/understanding-directory-structure/

categories:
  - Django
---

![](/post/129/django-file-structure.png)

**HelloWorld/**

This is our Django main project directory. It is just a container for our project hence we can rename this directory to anything.

**HelloWorld/manage.py**

manage.py is command line utility for interacting with your project.

**HelloWorld/HelloWorld/**

This is our project directory. It is the actual Python package for your project.

**HelloWorld/HelloWorld/\_\_init\_\_.py**

An empty file, which guides Python to treat the directory as a Python module

**HelloWorld/HelloWorld/settings.py**

As the name suggests, this file contains configuration for the project.

**HelloWorld/HelloWorld/urls.py**

This file contains URL pattern of the project.

**HelloWorld/HelloWorld/wsgi.py**

wsgi is Short for Web Server Gateway Interface. Hence this is the gateway file to wsgi-compatible servers or application. [More about WSGI can be read here](https://wsgi.readthedocs.io/en/latest/).
