---
id: 134
title: "Disable WordPress Formatted Entities"
date: "2021-02-09T08:48:52+05:30"
author: "Kunal Gautam"
layout: post

url: /kunal/2021/02/09/disable-wordpress-formatted-entities/

categories:
  - WordPress
---

Recently while I was working on my Linux blog, I noticed that WordPress started formatting "--" as "—", which was quite frustrating as commands become useless without proper attributes/switches.

The following is the table with list of text which Replaces common plain text characters with formatted entities.  
Information taken from [wptexturize()](https://developer.wordpress.org/reference/functions/wptexturize/)

| source text | transformed text | symbol name                        |
| ----------- | ---------------- | ---------------------------------- |
| "---"       | "—"              | em-dash                            |
| " -- "      | "—"              | em-dash                            |
| "--"        | "–"              | en-dash                            |
| " - "       | "–"              | en-dash                            |
| "..."       | "…"              | ellipsis                           |
| ``          | “                | opening quote                      |
| "hello      | “hello           | opening quote                      |
| 'hello      | ‘hello           | opening quote                      |
| ''          | ”                | closing quote                      |
| world."     | world.”          | closing quote                      |
| world.'     | world.’          | closing quote                      |
| " (tm)"     | " ™"             | trademark symbol                   |
| 1234"       | 1234″            | double prime symbol                |
| 1234'       | 1234′            | prime symbol                       |
| '99         | ’99              | apostrophe before abbreviated year |
| Webster's   | Webster’s        | apostrophe in a word               |
| 1234x1234   | 1234×1234        | multiplication symbol              |

To disable the wptexturize() function, one can add following to the function.php of currently activated theme or by creating a plugin

`add_filter('run_wptexturize', '__return_false');`

I've chosen to create a plugin and add the above code, as with changing theme, I don't need to worry about the problem arising again.
