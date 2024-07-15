>[!Related Topic:]
>[[Manages Table and Unmanaged Tables]]


Tables reside within a database. We  can create your own database name (also use default database). 

```python
spark.sql('Create table table_name')
spark.sql('Use table_name')
```

When already had a database, to create a within the database, we can use these sql commands:
```python
spark.sql("CREATE TABLE managed_table_name (date STRING, delay INT, distance INT")
```

You also can do the same thing using the DataFrame API like this:

```python

schema = "date STRING, delay INT, distance INT, origin STRING"

df = spark.read.csv(file_path, schema=schema)

df.write.saveAsTable("managed_table_name")
```








