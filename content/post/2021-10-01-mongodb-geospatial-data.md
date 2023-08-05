---
id: 148
title: "MongoDB | Geospatial Data"
date: "2021-10-01T03:27:54+05:30"
author: "Kunal Gautam"
layout: post

url: /kunal/2021/10/01/mongodb-geospatial-data/

categories:
  - "MongoDB Learning"
---

**Insert data**

```
db.places.insertOne({
      name: 'California Academy of Sciences',
      location: { type: 'Point', coordinates: [-122.4640133, 37.7690971] }
    })
```

Type is GeoJSON Object.

Cordinates need to be provided first value as Longitude and second value as latitude
