Views   is a scope of tables or data.

The view is like a table, once creating a view, we can query it as a table. But the difference here is the life cycle of these two objects. The table persists data even when the cluster is terminated, while the views disappper.

You can create a view from an existing table using SQL

```sql
CREATE OR REPLACE GLOBAL TEMP VIEW view_name AS
SELECT date, delay, origin, destination from table_name
```

 In Python

```python
df = spark.sql("SELECT date, delay, origin, destination FROM table_name WHERE condition")

df_2 = spark.sql("SELECT * FROM table_name_2)

df.createOrReplaceTempView(view_name)

df_2.createOrReplaceGlobalView(view_name_2 )
				 
```

Notice that when accessing a global temporary view you must use the prefix _global_temp.<view_name>_ , because Spark creates global temporary views in a global temporary database  called global_temp. In SQL, it likes

```sql
SELECT * FROM global_temp.table_name
```

The global view can be accessed over all of notebook.

