---
id: 141
title: "MongoDB | Query and Projections"
date: "2021-09-25T03:17:48+05:30"
author: "Kunal Gautam"
layout: post

url: /kunal/2021/09/25/mongodb-query-and-projections/

categories:
  - "MongoDB Learning"
---

## Query Selectors

### Comparison

For comparison of different BSON type values, see the [specified BSON comparison order](https://docs.mongodb.com/manual/reference/operator/query/../../bson-type-comparison-order/#bson-types-comparison-order).

| Name                                                                                     | Description                                                         |
| ---------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| [`$eq`](https://docs.mongodb.com/manual/reference/operator/query/eq/#op._S_eq "$eq")     | Matches values that are equal to a specified value.                 |
| [`$gt`](https://docs.mongodb.com/manual/reference/operator/query/gt/#op._S_gt "$gt")     | Matches values that are greater than a specified value.             |
| [`$gte`](https://docs.mongodb.com/manual/reference/operator/query/gte/#op._S_gte "$gte") | Matches values that are greater than or equal to a specified value. |
| [`$in`](https://docs.mongodb.com/manual/reference/operator/query/in/#op._S_in "$in")     | Matches any of the values specified in an array.                    |
| [`$lt`](https://docs.mongodb.com/manual/reference/operator/query/lt/#op._S_lt "$lt")     | Matches values that are less than a specified value.                |
| [`$lte`](https://docs.mongodb.com/manual/reference/operator/query/lte/#op._S_lte "$lte") | Matches values that are less than or equal to a specified value.    |
| [`$ne`](https://docs.mongodb.com/manual/reference/operator/query/ne/#op._S_ne "$ne")     | Matches all values that are not equal to a specified value.         |
| [`$nin`](https://docs.mongodb.com/manual/reference/operator/query/nin/#op._S_nin "$nin") | Matches none of the values specified in an array.                   |

### Logical

| Name                                                                                     | Description                                                                                               |
| ---------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| [`$and`](https://docs.mongodb.com/manual/reference/operator/query/and/#op._S_and "$and") | Joins query clauses with a logical `AND` returns all documents that match the conditions of both clauses. |
| [`$not`](https://docs.mongodb.com/manual/reference/operator/query/not/#op._S_not "$not") | Inverts the effect of a query expression and returns documents that do _not_ match the query expression.  |
| [`$nor`](https://docs.mongodb.com/manual/reference/operator/query/nor/#op._S_nor "$nor") | Joins query clauses with a logical `NOR` returns all documents that fail to match both clauses.           |
| [`$or`](https://docs.mongodb.com/manual/reference/operator/query/or/#op._S_or "$or")     | Joins query clauses with a logical `OR` returns all documents that match the conditions of either clause. |

### Element

| Name                                                                                                 | Description                                            |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------ |
| [`$exists`](https://docs.mongodb.com/manual/reference/operator/query/exists/#op._S_exists "$exists") | Matches documents that have the specified field.       |
| [`$type`](https://docs.mongodb.com/manual/reference/operator/query/type/#op._S_type "$type")         | Selects documents if a field is of the specified type. |

### Evaluation

| Name                                                                                                                 | Description                                                                                        |
| -------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| [`$expr`](https://docs.mongodb.com/manual/reference/operator/query/expr/#op._S_expr "$expr")                         | Allows use of aggregation expressions within the query language.                                   |
| [`$jsonSchema`](https://docs.mongodb.com/manual/reference/operator/query/jsonSchema/#op._S_jsonSchema "$jsonSchema") | Validate documents against the given JSON Schema.                                                  |
| [`$mod`](https://docs.mongodb.com/manual/reference/operator/query/mod/#op._S_mod "$mod")                             | Performs a modulo operation on the value of a field and selects documents with a specified result. |
| [`$regex`](https://docs.mongodb.com/manual/reference/operator/query/regex/#op._S_regex "$regex")                     | Selects documents where values match a specified regular expression.                               |
| [`$text`](https://docs.mongodb.com/manual/reference/operator/query/text/#op._S_text "$text")                         | Performs text search.                                                                              |
| [`$where`](https://docs.mongodb.com/manual/reference/operator/query/where/#op._S_where "$where")                     | Matches documents that satisfy a JavaScript expression.                                            |

### Geospatial

| Name                                                                                                                             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| -------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [`$geoIntersects`](https://docs.mongodb.com/manual/reference/operator/query/geoIntersects/#op._S_geoIntersects "$geoIntersects") | Selects geometries that intersect with a [GeoJSON](https://docs.mongodb.com/manual/reference/operator/query/../../glossary/#term-geojson) geometry. The [2dsphere](https://docs.mongodb.com/manual/reference/operator/query/../../../core/2dsphere/) index supports [`$geoIntersects`](https://docs.mongodb.com/manual/reference/operator/query/geoIntersects/#op._S_geoIntersects "$geoIntersects").                                                                                      |
| [`$geoWithin`](https://docs.mongodb.com/manual/reference/operator/query/geoWithin/#op._S_geoWithin "$geoWithin")                 | Selects geometries within a bounding [GeoJSON geometry](https://docs.mongodb.com/manual/reference/operator/query/../../geojson/#geospatial-indexes-store-geojson). The [2dsphere](https://docs.mongodb.com/manual/reference/operator/query/../../../core/2dsphere/) and [2d](https://docs.mongodb.com/manual/reference/operator/query/../../../core/2d/) indexes support [`$geoWithin`](https://docs.mongodb.com/manual/reference/operator/query/geoWithin/#op._S_geoWithin "$geoWithin"). |
| [`$near`](https://docs.mongodb.com/manual/reference/operator/query/near/#op._S_near "$near")                                     | Returns geospatial objects in proximity to a point. Requires a geospatial index. The [2dsphere](https://docs.mongodb.com/manual/reference/operator/query/../../../core/2dsphere/) and [2d](https://docs.mongodb.com/manual/reference/operator/query/../../../core/2d/) indexes support [`$near`](https://docs.mongodb.com/manual/reference/operator/query/near/#op._S_near "$near").                                                                                                       |
| [`$nearSphere`](https://docs.mongodb.com/manual/reference/operator/query/nearSphere/#op._S_nearSphere "$nearSphere")             | Returns geospatial objects in proximity to a point on a sphere. Requires a geospatial index. The [2dsphere](https://docs.mongodb.com/manual/reference/operator/query/../../../core/2dsphere/) and [2d](https://docs.mongodb.com/manual/reference/operator/query/../../../core/2d/) indexes support [`$nearSphere`](https://docs.mongodb.com/manual/reference/operator/query/nearSphere/#op._S_nearSphere "$nearSphere").                                                                   |

### Array

| Name                                                                                                             | Description                                                                                                                                                                                            |
| ---------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [`$all`](https://docs.mongodb.com/manual/reference/operator/query/all/#op._S_all "$all")                         | Matches arrays that contain all elements specified in the query.                                                                                                                                       |
| [`$elemMatch`](https://docs.mongodb.com/manual/reference/operator/query/elemMatch/#op._S_elemMatch "$elemMatch") | Selects documents if element in the array field matches all the specified [`$elemMatch`](https://docs.mongodb.com/manual/reference/operator/query/elemMatch/#op._S_elemMatch "$elemMatch") conditions. |
| [`$size`](https://docs.mongodb.com/manual/reference/operator/query/size/#op._S_size "$size")                     | Selects documents if the array field is a specified size.                                                                                                                                              |

### Bitwise

| Name                                                                                                                         | Description                                                                                         |
| ---------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| [`$bitsAllClear`](https://docs.mongodb.com/manual/reference/operator/query/bitsAllClear/#op._S_bitsAllClear "$bitsAllClear") | Matches numeric or binary values in which a set of bit positions _all_ have a value of `0`.         |
| [`$bitsAllSet`](https://docs.mongodb.com/manual/reference/operator/query/bitsAllSet/#op._S_bitsAllSet "$bitsAllSet")         | Matches numeric or binary values in which a set of bit positions _all_ have a value of `1`.         |
| [`$bitsAnyClear`](https://docs.mongodb.com/manual/reference/operator/query/bitsAnyClear/#op._S_bitsAnyClear "$bitsAnyClear") | Matches numeric or binary values in which _any_ bit from a set of bit positions has a value of `0`. |
| [`$bitsAnySet`](https://docs.mongodb.com/manual/reference/operator/query/bitsAnySet/#op._S_bitsAnySet "$bitsAnySet")         | Matches numeric or binary values in which _any_ bit from a set of bit positions has a value of `1`. |

### Comments

| Name                                                                                                     | Description                          |
| -------------------------------------------------------------------------------------------------------- | ------------------------------------ |
| [`$comment`](https://docs.mongodb.com/manual/reference/operator/query/comment/#op._S_comment "$comment") | Adds a comment to a query predicate. |

## Projection Operators

| Name                                                                                                                             | Description                                                                                                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [`$`](https://docs.mongodb.com/manual/reference/operator/query/../projection/positional/#proj._S_ "$")                           | Projects the first element in an array that matches the query condition.                                                                                                                                      |
| [`$elemMatch`](https://docs.mongodb.com/manual/reference/operator/query/../projection/elemMatch/#proj._S_elemMatch "$elemMatch") | Projects the first element in an array that matches the specified [`$elemMatch`](https://docs.mongodb.com/manual/reference/operator/query/../projection/elemMatch/#proj._S_elemMatch "$elemMatch") condition. |
| [`$meta`](https://docs.mongodb.com/manual/reference/operator/query/../aggregation/meta/#proj._S_meta "$meta")                    | Projects the document’s score assigned during [`$text`](https://docs.mongodb.com/manual/reference/operator/query/text/#op._S_text "$text") operation.                                                         |
| [`$slice`](https://docs.mongodb.com/manual/reference/operator/query/../projection/slice/#proj._S_slice "$slice")                 | Limits the number of elements projected from an array. Supports skip and limit slices.                                                                                                                        |
