---
id: 155
title: MongoDB | Importing data from CSV file
author: Kunal Gautam
type: post
date: 2021-10-07T22:06:10+00:00
url: /kunal/2021/10/08/mongodb-importing-data-from-csv-file/

categories:
  - MongoDB Learning
---

    mongoimport -h lan.ikunal.in --type csv -d hospitals -c list --headerline --drop hospital_directory.csv -u hospitals

- `–type:` The input format to import: json, csv, or tsv. We are using csv so that’s what we specify.
- `-d:` Specifies what database to use. We used the hospitals database.
- `-c:` Specifies what collection to use. We used a collection called list.
- `--headerline:` Specifies that the first row in our csv file should be the field names.
- `--drop:` Specifies that we want to drop the collection before importing documents.
- `-u:` specifys the user to log in
