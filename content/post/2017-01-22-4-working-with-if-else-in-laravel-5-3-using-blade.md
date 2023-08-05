---
id: 122
title: "Working With If Else in Laravel 5.3 using Blade"
date: "2017-01-22T16:18:57+05:30"
author: "Kunal Gautam"
layout: post

url: /kunal/2017/01/22/working-with-if-else-in-laravel-5-3-using-blade/

categories:
  - Laravel
tags:
  - Laravel
  - PHP
  - "PHP 7.0"
---

As we have seen in [earlier tutorial about Loops](https://blog.ikunal.in/kunal/2017/01/22/working-with-loops-in-laravel-5-3-using-blade/), let see how to use if statements in Blade Template engine.

## If Else Condition

<script src="https://gist.github.com/KunalGautam/66e5173306d8c206dd68c4ed7ab6055f.js"></script>

In above code, we have checked if $var is empty, if it is empty output It is empty, else output It is not empty. if condition can also be used for comparison. For example:

<script src="https://gist.github.com/KunalGautam/c15144ec3ab6af885709e85005b07a9f.js"></script>

## Unless statement

Unless is generally "if not" condition. For example:

<script src="https://gist.github.com/KunalGautam/25551f970eb554b14e769deb0c5d1e9d.js"></script>

In this example if $var is empty, it will not process this loop and exit.
