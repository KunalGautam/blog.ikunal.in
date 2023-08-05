---
id: 147
title: "MongoDB | Index"
date: "2021-09-30T03:27:10+05:30"
author: "Kunal Gautam"
layout: post

url: /kunal/2021/09/30/mongodb-index/

categories:
  - "MongoDB Learning"
---

**To get index lists**

```
db.tableName.getIndexes()
```

---

**To set Index**

```
db.contact.createIndex({age:1})
```

It will create index in asc order

```
db.contact.createIndex({age:-1})
```

It will create index in desc order

```
db.contact.createIndex({age:1, gender:1})
```

Create group of index with age and gender both done in asc order.

---

**To Delete Index**

```
db.contact.dropIndex({"age": 1})
```

Value of key need to be 1 or -1 based on how index was created. If asc, 1 and for desc it is -1

---

**Create Unique index**

```
db.contact.createIndex({email:1},{unique: true})
```

Create Unique Index on email field. While inserting data one have to provide email field, else it would throw error

```
db.users.createIndex({email: 1}, {unique: true, partialFilterExpression: {email: {$exists: true}}})
```

Only create index for email field if exists. If field doesn't exists, no issue even while inserting new data.

---

**TTL Index**

```
db.sessions.createIndex({createdAt: 1}, {expireAfterSeconds: 10})
```

create index for CreatedAt (the column should be datetime type) and destroy the record having that index after 10 seconds.
