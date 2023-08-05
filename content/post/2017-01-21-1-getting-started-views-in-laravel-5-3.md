---
id: 117
title: "Getting Started - Views in Laravel 5.3"
date: "2017-01-21T14:11:57+05:30"
author: "Kunal Gautam"
layout: post

url: /kunal/2017/01/21/getting-started-views-in-laravel-5-3/

categories:
  - Laravel
tags:
  - Laravel
  - PHP
  - "PHP 7.0"
---

In the[ last tutorial](https://blog.ikunal.in/kunal/2017/01/20/getting-started-hello-world-in-laravel-5-3/) we have seen a way to get text output. You can also return whole HTML code in the output, but that will make the routes file little bit ugly and hard to read. Instead of using HTML code there, **view** method is called. So whenever view method is called upon, it search for the view file inside the **resources/views** folder. These files are called blade template file. So let's get started with it.

First we will modify the '/' (root) route from the routes file i.e. we will edit **routes/web.php** file. Delete all content from that file and add following lines to it.

<script src="https://gist.github.com/KunalGautam/452e5589d26a044a935085f95547f477.js"></script>

In above code, we are returning **view** of **index**. The above code will call the **index.blade.php** file from **resources/views** folder. Since this file doesn't exists right now, we will create one. We will **create file** at **resources/views/index.blade.php** and add any HTML code which we would like to see.

Once done adding HTML code to the file, hit the **php artisan serve** command and visit our development site URL.

We can arrange views in folders. For example to access view file at **resources/views/somefolder/somesubfolder/somefile.blade.php** the return view will be like

<script src="https://gist.github.com/KunalGautam/5ab491b9c43c47574fcde348b74a2e91.js"></script>

In above example, each of the '.' (dot or period character) denotes a folder.
