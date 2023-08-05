---
id: 146
title: "MongoDB | Advanced Update Operators"
date: "2021-09-29T03:21:55+05:30"
author: "Kunal Gautam"
layout: post

url: /kunal/2021/09/29/mongodb-advanced-update-operators/

categories:
  - "MongoDB Learning"
---

```
db.users.updateOne({"_id" : ObjectId("11a")}, {$inc: {age: 2}})
```

Increment age by 2 for object id 11a

---

```
db.users.updateOne({"_id" : ObjectId("11a")}, {$inc: {age: -1}, $set: {exp: 22}})
```

Decrement age by 1 for object id 11a and set exp = 22

---

let assume a user Chris has age of 35

```
db.users.updateOne({name: "Chris"}, {$min: {age: 32}})
```

If age is more than 32, set age to 32. Chris age will change to 32

```
db.users.updateOne({name: "Chris"}, {$max: {age: 38}})
```

If age is less than 38, set age to 38. Chris age will change to 38 (as it was set to 32).

---

```
db.users.updateOne({name: "Chris"}, {$mul: {age: 1.1}})
```

Multiply age by 1.1

---

```
db.users.updateMany({isSporty: true}, {$unset: {phone: ""}})
```

Unset a field name phone. Need to provide an empty value to get it work.

---

```
db.users.updateMany({}, {$rename: {name: "FullName", age: "TotalAge"}})
```

Rename field named name to Full Name and age to Total Age.

---

```
db.users.updateOne({name: "Maria"}, {$set: {age: 26, hobbies: [{title: "Good food", frequency: 1}], isSporty: true}}, {upsert: true})
```

`upsert` as third param(Can be read as update or insert), can insert if not found, or if found it will update the value.

In above example, it will search for name Maria, if it exists it will update rest of the values, if it doesn't exisits, the new record will be created.

---

```
db.users.updateOne({name: "Maria"}, {$push: {hobbies: {title: "Sports", frequency: 2}}})
```

Push element with value if value exists, it will still add another element.

---

```
db.users.updateOne({name: "Maria"}, {$pull: {hobbies: {title: "Sports"}}})
```

Pull/Remove the element named Sports from hobbies

---

```
db.users.updateOne({name: "Maria"}, {$addToSet: {hobbies: {title: "Sports", frequency: 2}}})
```

Add element with value if value exists, it will not add add another element if value of the element is same. This is useful to avoid duplicate entry.

---
