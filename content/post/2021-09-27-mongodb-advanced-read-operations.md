---
id: 144
title: "MongoDB | Advanced Read Operations"
date: "2021-09-27T03:19:58+05:30"
author: "Kunal Gautam"
layout: post

url: /kunal/2021/09/27/mongodb-advanced-read-operations/

categories:
  - "MongoDB Learning"
---

```
db.users.find({}).sort({id: 1}).pretty()
```

`.sort()` with id in acending order

```
db.users.find({}).sort({id: -1}).pretty()
```

`.sort()` with id in decending order

```
db.users.find({}).sort({"ratings.average": -1}).pretty()
```

`.sort()` filter applied on average doocument/element under ratings with decending order

```
db.users.find({}).sort({"ratings.average": 1},{runtime: -1}).pretty()
```

`.sort()` in acending order by average ratings followed by runtime in decending order. eg. result will be like:

```
1) avgrating: 2, runtime 60
2) avgrating: 2, runtime 40
3) avgrating: 2, runtime 20
4) avgrating: 4.1, runtime 60
5) avgrating: 5, runtime 50
6) avgrating: 5, runtime 40
7) avgrating: 7.1, runtime 60
```

---

```
db.movies.find({}, {name: 1, _id: 0, "rating.average": 1, runtime: 1}).skip(10)
```

Skip first 10 result and show all result after 10th record

```
db.movies.find({}, {name: 1, _id: 0, "rating.average": 1, runtime: 1}).skip(100).limit(10)
```

Skip first 10 result and limit result to 10.

---

```
db.MoviesCollection.find({}, {genres: {$slice: 2}}).pretty()
```

Find all document but return only first two elements of genres in the result set.

```
db.MoviesCollection.find({}, {genres: {$slice: [1, 2]}}).pretty()
```

Find all document but return by skipping first element and display rest two elements of genres in the result set.
