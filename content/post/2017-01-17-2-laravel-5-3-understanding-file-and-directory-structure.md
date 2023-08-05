---
id: 115
title: "Laravel 5.3 Understanding File and Directory Structure"
date: "2017-01-17T16:41:25+05:30"
author: "Kunal Gautam"
layout: post

url: /kunal/2017/01/17/laravel-5-3-understanding-file-and-directory-structure/

categories:
  - Laravel
tags:
  - Laravel
  - PHP
  - "PHP 7.0"
---

Laravel follows the [model–view–controller](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller "Model–view–controller") (MVC) [architectural pattern](https://en.wikipedia.org/wiki/Architectural_pattern "Architectural pattern"). Hence the directory structure can be confusing for a person who is not much seen into MVCs. But It is very easy to understand.

I'll cover the basic directories which are mostly used. If anything you don't understand, I'd suggest to progress further, it will get clear by developing on the platform. So Let Get started with Directory Structure.

There are many files in your root of Application director. Some important one are:

**artisan**: It is end point for artisan command which is used for various tasks and function in Laravel.

**composer.json**: Dependency and all list for composer installation

**.env**: This file contain configuration based on the environment of the application.

**package.json**: This file contain node related dependency, for example compiling SASS or LESS.

**Upon installing following directories will be created**

- app
- bootstrap
- config
- database
- public
- resources
- routes
- storage
- tests
- vendor

## The `app` Directory

This directory contain core files of the application. it is further divided in following sub directory:

- **Console**: This contain custom artisan commands for the application
- **Exception**: This directory contain application exception handler.
- **Http**: This directory contain controllers &amp; middleware. They are placed in their respective directories.
- **Providers**: This directory contains service provider for your application. For example by default Laravel comes with Authentication provider which when enabled, is used for authentication purposes.

## The `config` Directory

As you have gussed by the name of the directory, it contains all of your application's configuration files.

## The `database` Directory

This directory contain database migration and seeds. If you don't know what is database migration and seeds, don't worry it will be covered in upcoming posts.

## The `public` Directory

This is the main directory where entry point index. php file is place. While running from server, this should be the point from where the application can be called on. Alternatively, images, JS and CSS are fetched from this directory

## The `resources` Directory

This directory contains raw, uncompiled assets such as LESS, SASS or JS. It also contain template and language files for the application.

## The `routes` Directory

This directory contain the route files, i.e. something like pretty URL for your application and its corresponding views. It will get more clear in upcoming posts.

## The `storage` Directory

It contains compiled templates, caches and logs file.

## The `test` Directory

It contain automated test for your php application. [PHPUnit](https://phpunit.de/) is provided out of the box.

## The `vendor` Directory

It contain various supporting frameworks, codes and dependencies to make application working.
