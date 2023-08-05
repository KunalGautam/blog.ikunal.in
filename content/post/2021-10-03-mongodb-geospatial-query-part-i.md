---
id: 150
title: "MongoDB | Geospatial Query Part - I"
date: "2021-10-03T03:32:06+05:30"
author: "Kunal Gautam"
layout: post

url: /kunal/2021/10/03/mongodb-geospatial-query-part-i/

categories:
  - "MongoDB Learning"
---

First we need to set index as 2dsphere

```
db.places.createIndex({location: "2dsphere"})
```

Then provide the input to find nearby. Distance is in Meters.

```
db.places
  .find({
    location: {
      $near: {
        $geometry: { type: 'Point', coordinates: [-122.4626966, 37.7694006] },
        $maxDistance: 130,
        $minDistance: 10
      }
    }
  })
  .pretty();
```

---

**To Find withing Polygon area**

Setting points of polygon

```
const p1 = [-122.45476, 37.77488]
const p2 = [-122.453, 37.76637]
const p3 = [-122.5104, 37.76397]
const p4 = [-122.51115, 37.77134]
```

Perform Query

```
db.places
      .find({
        location: {
          $geoWithin: {
            $geometry: { type: 'Polygon', coordinates: [[p1, p2, p3, p4, p1]] }
          }
        }
      })
      .pretty();
```
