---
id: 136
title: "MongoDB | Getting Started"
date: "2021-09-18T08:39:24+05:30"
author: "Kunal Gautam"
layout: post

url: /kunal/2021/09/18/getting-started/

categories:
  - "MongoDB Learning"
---

**All commands mentioned need to be run on mongo shell**

## 1) To see list of database

`show dbs`

It will show list of Databases along with the size. If a databse is empty, it won't be shown by the command.

## 2) To use a database

`use databaseName`

It will switch to the databaseName databse (If database won't exists, it will create one)

## 3) To see which database is in use

`db`

It will return the database currently in use

## 4) Seeking Help

`db.help()`

To show available functions

`db.databaseName.help()`

To show available functions with database

## 5) Delete Database

`db.dropDatabase()`

To drop the database

---

**Note:**

- If familiar with SQL, the tables are called collections and records are called documents in MongoDB
