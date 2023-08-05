---
id: 131
title: "Create a Database Connected WebApp (Part I)"
date: "2019-07-15T17:42:49+05:30"
author: "Kunal Gautam"
layout: post

url: /kunal/2019/07/15/create-a-database-connected-webapp-part-i/

categories:
  - Django
---

In this post we will install MySQL connector for Python for getting started with Database connected Application on Django.

**On MAC OS X, following additional steps need to be done for installing the Database connector, others can skip directly to Installing MySQL connector for Python.**

First we need to install mysql-client on the system, so that the MySQL driver can be installed properly using pip. To do so, [install homebrew](https://brew.sh/) if not installed. Once homebrew is installed, install mysql-client binary by using following command

`brew install mysql-client`

It will install mysql-client on your system. To make mysql-client available over terminal, add the following to your [.zshrc](https://superuser.com/a/886135) or [.bashrc](https://askubuntu.com/a/540689) file.

`export PATH="/usr/local/opt/openssl@1.1/bin:$PATH"`  
`export PATH="/usr/local/opt/mysql-client/bin:$PATH"`

Also add the following environment variable in your [.zshrc](https://superuser.com/a/886135) or [.bashrc](https://askubuntu.com/a/540689) file for SSL binary which get installed with mysql-client binary

`export LDFLAGS="-L/usr/local/opt/openssl@1.1/lib"`  
`export CPPFLAGS="-I/usr/local/opt/openssl@1.1/include"`

Now restart your terminal, and you will be good to go.

### Installing MySQL Connector for Python

Install MySQL Connector by passing following command to the terminal.

`pip install mysqlclient`

[In second part, we will use mysqlclient package to connect our Application with the database.](https://blog.ikunal.in/kunal/2019/07/15/create-a-database-connected-webapp-part-ii/)
