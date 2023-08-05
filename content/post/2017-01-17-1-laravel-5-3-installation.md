---
id: 114
title: "Laravel 5.3 Installation"
date: "2017-01-17T15:59:36+05:30"
author: "Kunal Gautam"
layout: post

url: /kunal/2017/01/17/laravel-5-3-installation/

image: /wp-content/uploads/2017/01/LaravelLogo.png
categories:
  - Laravel
tags:
  - Laravel
  - PHP
  - "PHP 7.0"
---

Laravel need following perquisites to get working:

- PHP &gt;= 5.6.4
- OpenSSL PHP Extension
- PDO PHP Extension
- Mbstring PHP Extension
- Tokenizer PHP Extension
- XML PHP Extension

I will be using PHP 7.0 along with mysql for my database requirement.

There may be different way to install Laravel project, but as per official documentation, it utilize [Composer](https://getcomposer.org/) to manage its dependencies. To install Composer one can [follow instructions at their official website which can be found here.](https://getcomposer.org/doc/00-intro.md)

After installing composer, we will install Laravel globally. Installing Laravel globally helps to utilize Laravel command anywhere. To install 'laravel' as command, pass the following command in your terminal.

**`composer global require "laravel/installer"`**

The screen will show where the laravel files are getting installed. Note down that path. In my case the files got stored on **~/.config/composer/**

For enabling 'laravel' command, we will add the following line in shell config file. Since I use Bash Shell, the config file will be located at **~/.bashrc**

`<strong>export PATH "~/.config/composer/vendor/bin:$PATH"</strong>`

Close and run shell again to see 'laravel' command. Pass **'laravel'** command in your shell. If everything is working fine, you will be greeted with laravel installer showing Laravel installer version, options and available commands.

Next navigate to your desired folder where you want to install your new Laravel project, and pass the following command.

`<strong>laravel new project_name</strong>`

As you have guessed, you can replace project_name with anything. The above command will install Laravel into the project_name directory and might take a while depending on your internet connection speed.
