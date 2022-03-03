---
id: nph9tuw7ad36ey6h83hcv9b
title: Commands
desc: ''
updated: 1646307570378
created: 1646305983951
---

#### List Datasets
```bash
bq ls
```

#### List Tables in Dataset
```bash 
bq ls datasetID
```

#### Create Dataset
```bash
bq mk datasetName
```

#### Load Data to a Table
```bash
bq load datasetName.tableName source_file.txt name:string,gender:string,count:integer
```
where `name:...` is the schema definition for the table.

#### Examine table schema
```bash
bq show project:dataset.table
```

#### Run a query 
```bash
bq query --use_legacy_sql=false \
'SELECT
   word,
   SUM(word_count) AS count
 FROM
   `bigquery-public-data`.samples.shakespeare
 WHERE
   word LIKE "%raisin%"
 GROUP BY
   word'
```

#### Remove a Dataset
```bash
bq rm -r babynames
```