---
id: zxkjp90w6rcw3yg6yrmiitv
title: Pyspark
desc: ''
updated: 1674233435779
created: 1673977835232
---

# Selecting columns

```python
df.select("column_name")
```

## Filtering

Filter rows to those that are not null
    
```python
df.filter(df.column_name.isNotNull())
```

## Count unique

```python
df.select("column_name").distinct().count()
```
