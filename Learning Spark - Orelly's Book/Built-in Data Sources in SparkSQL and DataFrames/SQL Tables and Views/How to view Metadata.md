Spark manages the metadata associated with each managed or unmanaged table.

The metadata is captured in the _Catalog_, a high-level abstraction in Spark SQL for storing metadata. You can check it in Python

```python
spark.catalog.listDatabases()
spark.catalog.listTables()
spark.catalog.listColumns(table_name)
```

