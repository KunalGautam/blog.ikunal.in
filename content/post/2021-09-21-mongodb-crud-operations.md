---
id: 137
title: "MongoDB | CRUD Operations"
date: "2021-09-21T03:10:59+05:30"
author: "Kunal Gautam"
layout: post

url: /kunal/2021/09/21/mongodb-crud-operations/

categories:
  - "MongoDB Learning"
---

## 1) Creating Record:

Record can be inserted using:

```
db.tableName.insert()
db.tableName.insertOne()
db.tableName.insertMany()
```

- **.insert()** can accept single or multiple records. Returns WriteResult/BulkWriteResult.

Example showing inserting one record

```
db.tableName.insert(
{
name: "John",
age: 23,
skills: {
    programming: "PHP, Java, Python",
    database: "MongoDB, SQLITE"
}
}
)
```

Example showing Multiple Records

```
db.inventory.insert([
   { item: "journal", qty: 25, status: "A", size: { h: 14, w: 21, uom: "cm" }, tags: [ "blank", "red" ] },
   { item: "notebook", qty: 50, status: "A", size: { h: 8.5, w: 11, uom: "in" }, tags: [ "red", "blank" ] },
   { item: "paper", qty: 10, status: "D", size: { h: 8.5, w: 11, uom: "in" }, tags: [ "red", "blank", "plain" ] },
   { item: "planner", qty: 0, status: "D", size: { h: 22.85, w: 30, uom: "cm" }, tags: [ "blank", "red" ] },
   { item: "postcard", qty: 45, status: "A", size: { h: 10, w: 15.25, uom: "cm" }, tags: [ "blue" ] }
])
```

---

- **.insertOne()** accept one record at a time. Returns record id inserted.

```
db.tableName.insertOne(
{
name: "John",
age: 23,
skills: {
    programming: "PHP, Java, Python",
    database: "MongoDB, SQLITE"
}
}
)
```

---

- **.insetMany()** accept multiple record at a time. Return record ids inserted.

```
db.inventory.insertMany([
   { item: "journal", qty: 25, status: "A", size: { h: 14, w: 21, uom: "cm" }, tags: [ "blank", "red" ] },
   { item: "notebook", qty: 50, status: "A", size: { h: 8.5, w: 11, uom: "in" }, tags: [ "red", "blank" ] },
   { item: "paper", qty: 10, status: "D", size: { h: 8.5, w: 11, uom: "in" }, tags: [ "red", "blank", "plain" ] },
   { item: "planner", qty: 0, status: "D", size: { h: 22.85, w: 30, uom: "cm" }, tags: [ "blank", "red" ] },
   { item: "postcard", qty: 45, status: "A", size: { h: 10, w: 15.25, uom: "cm" }, tags: [ "blue" ] }
])
```

---

## 2. Reading Record

- To see all tables (It is called as collections)

```
show collections
```

- To read all records

```
db.tableName.find()
```

or

```
db.tableName.find({})
```

- To return data in readable format

```
  db.tableName.find().pretty()
```

- To find a record with name = John inside tableName table:

```
db.tableName.find({name: "John"})
```

- To find all record returning name key:

```
db.tableName.find({}, {name:1})
```

or to exclude \_id

```
db.tableName.find({}, {name:1, _id:0})
```

---

## 3. Modifying/Update the Record

`*Note: If the field to be update doesn't exsists, it will be added, else it will be updated*`

**To update all record in the table**

```
db.tableName.updateMany({}, {$set: {status: "Active"}})
```

**To update all record matching query**

Update data from table where name = John

```
db.tableName.updateMany({name: "John"}, {$set: {status: "Inactive"}})
```

**To update first matching query record**

```
db.tableName.updateOne({name: "John"}, {$set: {status: "Active"}})
```

**Overwrite/Replace record**  
update record with name = john by deleting exsisting keys and values and add newKey with Value

```
db.tableName.update({name: "John"}, {newKey: "Value"})
```

**Replace Record**

```
db.tableName.replaceOne({_id: ObjectId("sh9oiulukskji")}, {newKey: "Value"})
```

---

## 4. Deleting Record

**To delete all record matching query**

Delete data from table where name = John

```
db.tableName.deleteMany({name: "John"})
```

**To delete one First matching query record**

```
db.tableName.deleteOne({name: "John"})
```

**Delete all records**

```
db.tableName.remove()
```

**Delete Table/Collections**

```
db.tableName.drop()
```

---

---

**Notes:**

- **.find()** won't return all records if record set is large. For example out of 100 Record it will return 10 and wait for input for fetching next 10 records. It is like pagination. to view all data we can use **.forEach()** function. e.g.

```
db.tableName.find({}).forEach((data)=>{printjson(data)})
```
