---
id: 151
title: "MongoDB | Geospatial Query Part - II"
date: "2021-10-04T03:33:02+05:30"
author: "Kunal Gautam"
layout: post

url: /kunal/2021/10/04/mongodb-geospatial-query-part-ii/

categories:
  - "MongoDB Learning"
---

Let say we need to find if user is within polygon area.

**Setting points of polygon**

```
const p1 = [-122.45476, 37.77488]
const p2 = [-122.453, 37.76637]
const p3 = [-122.5104, 37.76397]
const p4 = [-122.51115, 37.77134]
```

```
db.areas.insertOne({
      name: 'Golden Gate Park',
      area: { type: 'Polygon', coordinates: [[p1, p2, p3, p4, p1]] }
    })
```

**Set Index.**

```
db.areas.createIndex({area: "2dsphere"})
```

**Find if Point inside polygon area**

```
db.areas
      .find({
        area: {
          $geoIntersects: { $geometry: { type: 'Point', coordinates: [-122.463792, 37.768638] } }
        }
      })
      .pretty();
```

```
db.areas
      .find({
        area: {
          $geoIntersects: { $geometry: { type: 'Point', coordinates:[-122.4436619, 37.774995] } }
        }
      })
      .pretty();
```

`geoIntersects` helps to find out area within polygon defined.
