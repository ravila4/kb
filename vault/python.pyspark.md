---
id: zxkjp90w6rcw3yg6yrmiitv
title: Pyspark
desc: ''
updated: 1675024533761
created: 1673977835232
---

# Creating Dataframes

## From a csv

```python
df = spark.read.csv("data.csv", header=True)
```

## From pandas

```python
df = spark.createDataFrame(pandas_df)
```

# Selections

## Selecting columns

```python
df.select("column_name")
```

## Filtering

Filter rows to those that are not null
    
```python
df.filter(df.column_name.isNotNull())
```

Filter based on the length of an array column

```python
df.filter(size(df.column_name) > 0)
```

## Count unique

```python
df.select("column_name").distinct().count()
```

# Transformations

## Add a new column

With a constant value:

```python
df.withColumn("new_column", lit(1))
```

From another column:

```python
df.withColumn("new_column", df.column_name + 1)
```
## UDFs

Create a udf and apply it to a column:

```python
from pyspark.sql.functions import udf
from pyspark.sql.types import IntegerType

def add_one(x):
    return x + 1

add_one_udf = udf(add_one, IntegerType())

df.withColumn("new_column", add_one_udf(df.column_name))
```

## GroupBy and Aggregate

Aggreagate a dataframe by counting the number of rows in each group:

```python
df.groupBy("column_name").count()
```

Aggreagate a dataframe by counting the number of rows in each group, and sort by count:

```python
df.groupBy("column_name").count().orderBy("count", ascending=False)
```

Aggregate a dataframe by the number of unique values in a column:

```python
df.groupBy("column_name").agg(countDistinct("column_name"))
```

Group a dataframe by a column and aggregate by a udf

```python
from pyspark.sql.functions import udf
from pyspark.sql.types import IntegerType

def add_one(x):
    return x + 1

add_one_udf = udf(add_one, IntegerType())

df.groupBy("column_name").agg(add_one_udf("column_name"))
```

## Joining

Left join two dataframes on two common columns:

```python
df1.join(
    df2, [df1.column_name1 == df2.column_name1,
          df1.column_name2 == df2.column_name2],
    "left"
)
```
