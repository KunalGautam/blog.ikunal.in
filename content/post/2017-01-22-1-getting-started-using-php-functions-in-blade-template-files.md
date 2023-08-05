---
id: 119
title: "Getting Started - Using PHP functions in blade template files"
date: "2017-01-22T15:35:26+05:30"
author: "Kunal Gautam"
layout: post

url: /kunal/2017/01/22/getting-started-using-php-functions-in-blade-template-files/

categories:
  - Laravel
tags:
  - Laravel
  - PHP
  - "PHP 7.0"
---

There are many useful PHP functions which an developer might use from time to time in their application. To use PHP in a blade there are two methods:

1. Traditional method
2. Blade Template method

## Traditional Method

You can simply insert your PHP code within php tags and it will work. For example:

<script src="https://gist.github.com/KunalGautam/c350819c8cd86e1b8a0508d4e6a2ebe2.js"></script>

The above will echo something like: Sunday 22nd of January 2017 09:25:00 PM

But it is good and easy to use Blade Template method.

## Blade Template Method

above PHP code can be passed as following way:

<script src="https://gist.github.com/KunalGautam/3330810923c20e7f9bb93531c56fe3cd.js"></script>

So in above example, @php and @endphp is replaced as &lt;?php and ?&gt;
