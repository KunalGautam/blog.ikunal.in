---
id: 145
title: MongoDB | Update Operators
author: Kunal Gautam
type: post
date: 2021-09-28T03:21:06+00:00
url: /kunal/2021/09/28/mongodb-update-operators/

categories:
  - MongoDB Learning
---

### Fields {#h3-fields}

| Name                | Description                                                                                                                                   |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| [`$currentDate`][1] | Sets the value of a field to current date, either as a Date or a Timestamp.                                                                   |
| [`$inc`][2]         | Increments the value of the field by the specified amount.                                                                                    |
| [`$min`][3]         | Only updates the field if the specified value is less than the existing field value.                                                          |
| [`$max`][4]         | Only updates the field if the specified value is greater than the existing field value.                                                       |
| [`$mul`][5]         | Multiplies the value of the field by the specified amount.                                                                                    |
| [`$rename`][6]      | Renames a field.                                                                                                                              |
| [`$set`][7]         | Sets the value of a field in a document.                                                                                                      |
| [`$setOnInsert`][8] | Sets the value of a field if an update results in an insert of a document. Has no effect on update operations that modify existing documents. |
| [`$unset`][9]       | Removes the specified field from a document.                                                                                                  |

### <a class="reference-link" name="Array"></a>Array {#h3-array}

#### <a class="reference-link" name="Operators"></a>Operators {#h4-operators}

| Name                    | Description                                                                                                                            |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| [`$`][10]               | Acts as a placeholder to update the first element that matches the query condition.                                                    |
| [`$[]`][11]             | Acts as a placeholder to update all elements in an array for the documents that match the query condition.                             |
| [`$[<identifier>]`][12] | Acts as a placeholder to update all elements that match the `arrayFilters` condition for the documents that match the query condition. |
| [`$addToSet`][13]       | Adds elements to an array only if they do not already exist in the set.                                                                |
| [`$pop`][14]            | Removes the first or last item of an array.                                                                                            |
| [`$pull`][15]           | Removes all array elements that match a specified query.                                                                               |
| [`$push`][16]           | Adds an item to an array.                                                                                                              |
| [`$pullAll`][17]        | Removes all matching values from an array.                                                                                             |

#### <a class="reference-link" name="Modifiers"></a>Modifiers {#h4-modifiers}

| Name              | Description                                                                                            |
| ----------------- | ------------------------------------------------------------------------------------------------------ |
| [`$each`][18]     | Modifies the [`$push`][16] and [`$addToSet`][13] operators to append multiple items for array updates. |
| [`$position`][19] | Modifies the [`$push`][16] operator to specify the position in the array to add elements.              |
| [`$slice`][20]    | Modifies the [`$push`][16] operator to limit the size of updated arrays.                               |
| [`$sort`][21]     | Modifies the [`$push`][16] operator to reorder documents stored in an array.                           |

### <a class="reference-link" name="Bitwise"></a>Bitwise {#h3-bitwise}

| Name         | Description                                                        |
| ------------ | ------------------------------------------------------------------ |
| [`$bit`][22] | Performs bitwise `AND`, `OR`, and `XOR` updates of integer values. |

[1]: https://docs.mongodb.com/manual/reference/operator/update/currentDate/#up._S_currentDate "$currentDate"
[2]: https://docs.mongodb.com/manual/reference/operator/update/inc/#up._S_inc "$inc"
[3]: https://docs.mongodb.com/manual/reference/operator/update/min/#up._S_min "$min"
[4]: https://docs.mongodb.com/manual/reference/operator/update/max/#up._S_max "$max"
[5]: https://docs.mongodb.com/manual/reference/operator/update/mul/#up._S_mul "$mul"
[6]: https://docs.mongodb.com/manual/reference/operator/update/rename/#up._S_rename "$rename"
[7]: https://docs.mongodb.com/manual/reference/operator/update/set/#up._S_set "$set"
[8]: https://docs.mongodb.com/manual/reference/operator/update/setOnInsert/#up._S_setOnInsert "$setOnInsert"
[9]: https://docs.mongodb.com/manual/reference/operator/update/unset/#up._S_unset "$unset"
[10]: https://docs.mongodb.com/manual/reference/operator/update/positional/#up._S_ "$"

[11]: https://docs.mongodb.com/manual/reference/operator/update/positional-all/#up._S_[] "$[]"
 [12]: https://docs.mongodb.com/manual/reference/operator/update/positional-filtered/#up._S_[<identifier>] "$[<identifier>]"
[13]: https://docs.mongodb.com/manual/reference/operator/update/addToSet/#up._S_addToSet "$addToSet"
 [14]: https://docs.mongodb.com/manual/reference/operator/update/pop/#up._S_pop "$pop"
[15]: https://docs.mongodb.com/manual/reference/operator/update/pull/#up._S_pull "$pull"
 [16]: https://docs.mongodb.com/manual/reference/operator/update/push/#up._S_push "$push"
[17]: https://docs.mongodb.com/manual/reference/operator/update/pullAll/#up._S_pullAll "$pullAll"
 [18]: https://docs.mongodb.com/manual/reference/operator/update/each/#up._S_each "$each"
[19]: https://docs.mongodb.com/manual/reference/operator/update/position/#up._S_position "$position"
 [20]: https://docs.mongodb.com/manual/reference/operator/update/slice/#up._S_slice "$slice"
[21]: https://docs.mongodb.com/manual/reference/operator/update/sort/#up._S_sort "$sort"
 [22]: https://docs.mongodb.com/manual/reference/operator/update/bit/#up._S_bit "$bit"
