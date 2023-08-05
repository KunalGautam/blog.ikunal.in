---
id: 143
title: "MongoDB | Read Operation with Arrays"
date: "2021-09-26T03:18:45+05:30"
author: "Kunal Gautam"
layout: post

url: /kunal/2021/09/26/mongodb-read-operation-with-arrays/

categories:
  - "MongoDB Learning"
---

```
db.MoviesCollection.find({genres: {$size: 3}})
```

Find all generes which has size of 3 elements/documents

---

```
db.movieStarts.find({genre: { $all: ["action", "thriller"]}}, {title: 1, genre: 1, _id:0 })
```

Find all generes having action and thriller element. If $all is not used, it will search for the particular order and which is not what we might want.

---

```
db.users.find({ hobbies: { $elemMatch: { title:  'sports', frequency: { $gte:  3 } } } }).pretty()
```

Find all hobbies with element having sports and frequency Greater than or eqals to 3.
