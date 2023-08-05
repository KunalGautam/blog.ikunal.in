---
id: 153
title: "MongoDB | Geospatial Query Additional Notes"
date: "2021-10-06T03:34:37+05:30"
author: "Kunal Gautam"
layout: post

url: /kunal/2021/10/06/mongodb-geospatial-query-additional-notes/

categories:
  - "MongoDB Learning"
---

**$near** returns "nearest" as the naming suggests. And funny enough **$geoWithin** means "within the specified boundaries". In short, **$near** "sorts" the results to return, and that is always going to take more time than not sorting. So it depends on what you want. If "order" of "nearest" is important, then you use **$near**. If it is not, then use **$geoWithin** and a plain definition of a circle. Which is the only polygon the two share in common.
