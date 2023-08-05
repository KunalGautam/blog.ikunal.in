---
id: 130
title: "Turn your First Project to Hello World!"
date: "2019-07-15T14:35:19+05:30"
author: "Kunal Gautam"
layout: post

url: /kunal/2019/07/15/turn-your-first-project-to-hello-world/

categories:
  - Django
---

As we seen in [last post](https://blog.ikunal.in/kunal/2019/07/15/creating-and-run-your-first-project/), the application shows default Django page and not the "Hello World!" string. Isn't it sad?

In this post we will see how to create a "Hello World!" page inside Django application.

**Step1: Create View**

Create a new file named **views.py** inside **HelloWorld** directory and use this code :

 <script src="https://gist.github.com/KunalGautam/bef9489b38d2a41e295aec7720cdce5f.js"></script>

**Step2: Set the URL Pattern**

Open the **urls.py** file and use this code :

 <script src="https://gist.github.com/KunalGautam/1759a33fd14d08c9f4ca33e5ece27a1b.js"></script>

**Final Step: Run the server**

`python manage.py runserver `

To terminate/stop the server, press **CTRL+c** key
