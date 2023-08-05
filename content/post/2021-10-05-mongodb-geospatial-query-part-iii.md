---
id: 152
title: "MongoDB | Geospatial Query Part - III"
date: "2021-10-05T03:33:43+05:30"
author: "Kunal Gautam"
layout: post

url: /kunal/2021/10/05/mongodb-geospatial-query-part-iii/

categories:
  - "MongoDB Learning"
---

Find within Radius.

```
db.places
      .find({
        location: {
          $geoWithin: {
            $centerSphere: [[-122.462621, 37.770100], (1 / 6378.1)]
          }
        }
      })
      .pretty()
```

It takes two arguments, first cordinates and second radians for distance value. For 1 Km radian value is `1 / 6378.1` for 2 Km it is `2 / 6378.1`. For 1 mile it is `1 / 3963.2`
