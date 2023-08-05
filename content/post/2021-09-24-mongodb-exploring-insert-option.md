---
id: 140
title: "MongoDB | Exploring Insert Option"
date: "2021-09-24T03:15:43+05:30"
author: "Kunal Gautam"
layout: post

url: /kunal/2021/09/24/mongodb-exploring-insert-option/

categories:
  - "MongoDB Learning"
---

```
db.tableName.insertMany([{_id: 1, name: 1}, {_id: 2, name: 2}, {_id: 3, name: 3}])
```

This will insert documents. In case let assume name:2 is already in database, it will insert name:1 and throw error. the name: 3 won't be inserted in default behaviour. To get new document inserted and skip the already inserted documents, we can use:

```
db.tableName.insertMany([{_id: 1, name: 1}, {_id: 2, name: 2}, {_id: 3, name: 3}], {ordered: false})
```

The argument ordered: false will insert document which are not present in the document. By default the ordered is set to true.

---

```
mongoimport Downloads/tv-shows.json -d MoviesData -c MoviesCollection --jsonArray
```

import document from json file, -d creates database if not exists, -c create collection if not exsist, --jsonArray if the document contain array of documents.

---

<https://docs.mongodb.com/manual/reference/write-concern/>
