---
id: 118
title: "Getting Started - Where to store my CSS and JS in Laravel 5.3?"
date: "2017-01-21T14:15:17+05:30"
author: "Kunal Gautam"
layout: post

url: /kunal/2017/01/21/getting-started-where-to-store-my-css-and-js-in-laravel-5-3/

categories:
  - Laravel
tags:
  - Laravel
  - PHP
  - "PHP 7.0"
---

So now a nice HTML page can be designed, it is common practice to use CSS and JS externally in page. The question arises, where to store our CSS and JS files to be used with Laravel?

All CSS &amp; JS should be placed under **public** directory under root of your project directory. It can be called in blade file as

`{{ URL::asset('css/cssfile.css') }}`

For example a css.css file from css folder under public directory ( public/css/css.css) can be called as :

`<link href="{{ URL::asset('css.css') }}" rel="stylesheet">`

Alternatively, if you don't want to go this long, you can call it directly as:

`<link href="css/css.css" rel="stylesheet">`

The above example is also valid for JS files. Now the question arises, why there is JS and CSS folder inside **resources** folder?

The answer is those are file which are uncompiled and need to compiled using proper compiler. For example app related CSS can be there with SASS or LESS code and it will be compiled with required package and used within the app. We will cover that in upcoming tutorials.
