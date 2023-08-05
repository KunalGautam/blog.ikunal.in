---
id: 120
title: "Blade Template - Beginners level tips for Laravel 5.3"
date: "2017-01-22T16:05:43+05:30"
author: "Kunal Gautam"
layout: post

url: /kunal/2017/01/22/blade-template-beginners-level-tips-for-laravel-5-3/

categories:
  - Laravel
tags:
  - Laravel
  - PHP
  - "PHP 7.0"
---

[As we have seen in previous tutorial ](https://blog.ikunal.in/kunal/2017/01/22/getting-started-using-php-functions-in-blade-template-files/)we have echoed date. In this tutorial we will learn some more advance stuffs in blade template engine

Now the above example can be further simplified using only following code :

`{{  echo date('l jS \of F Y h:i:s A'); }}`

The curly brackets used are template shortcut for echo function. But double curly brackets are used to prevent the code from XSS attacks by stripping HTML entities. To overcome this we can use

{!! echo date('l jS \\of F Y h:i:s A'); !!}

Lets take an example to understand this. If you pass data from your controller to view with some styling like as  
**`$var = "<b>Hello</b>";`**  
and if it is accessed within blade with `{{ $var }}`

then the output'll be  
**`Hello`**  
and if it is accessed within blade with `{!! $var !!}`

then the output'll be

**Hello**

Now the question arises, what if I have to use {{ $var }} in my code, for eg. in angular js, variables are called that way only, how to do it. It is pretty simple: use:

`@{!! $var !!}`

In case you want to comment anything in your blade file, it can be done as following:

`{{ -- This is comment, and will not be rendered in HTML output --}} `

In starting you might feel little bit awkward to use these new things, but in long run it not only makes code look more cleaner, but also very easy to understand. In next tutorial we will see how to use for loop
