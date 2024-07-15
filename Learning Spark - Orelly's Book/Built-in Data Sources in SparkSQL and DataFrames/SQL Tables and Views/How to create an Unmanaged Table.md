Raleted topic: [[Manages Table and Unmanaged Tables]] , [[How to create a Managed Table in Spark]]

We can create unmanaged tables from a data source such as CSV, in SQL it likes:

```python
spark.sql("""CREATE TABLE table_name(date STRING, delay INT, distance INT)

USING csv OPTIONS (PATH file_path)""")
```





