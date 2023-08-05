---
id: 123
title: Controllers in Laravel 5.3
author: Kunal Gautam
type: post
date: 2017-01-23T15:56:10+00:00
url: /kunal/2017/01/23/controllers-in-laravel-5-3/

categories:
  - Laravel
tags:
  - Laravel
  - PHP
  - PHP 7.0
---

<p style="text-align: justify;">
  As we have seen in <a href="https://blog.ikunal.in/kunal/2017/01/23/getting-started-passing-arguments-to-view-in-laravel-5-3/">previous example of passing arguments to view</a>, the route file actually looks ugly and hard to read. As we know Laravel use <a href="https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller">MVC (Model View Controller)</a> , it is best to use a controller for that example. In short it is best to include any logic in controller. A controller may have one or more than one action.
</p>

<p style="text-align: justify;">
  Lets understand controller with an example. To create an <a href="https://en.wikipedia.org/wiki/Boilerplate_code">boilerplate</a> code for an controller we have to pass following command in root of the project directory.
</p>

`php artisan make:controller UsersController`

<p style="text-align: justify;">
  The above command will create UsersController.php file under <strong>app/Http/Controllers/ </strong>directory with the required boilerplate.
</p>

<p style="text-align: justify;">
  Now we will delete the users route and replace this with following code:
</p>

<p style="text-align: justify;">
  By saving the file and running laravel development server, we will see the same output. This time logic are placed inside controller file. This not only make code readable, but very easy to understand. Consider scenario where there are lot of users related function such as create, delete etc. All logic will be placed inside this controller file under different function/method. And we will call required function in the routes file. Example is given below.
</p>

<p style="text-align: justify;">
  <code>Route::post('users', 'UsersController@create');</code>
</p>

<p style="text-align: justify;">
  <code>Route::delete('users', 'UsersController@delete');</code>
</p>

&nbsp;

&nbsp;
