Spark allows us to create 2 types of table: **managed** and **unmanaged**

For a managed table, Spark manages both the metadata and the data in the file store. This could be a local file system, HDFS, or Amazon S3, Azure Blob

For unmanaged tables, Spark only manages the metadata, while data is stored in the external storages.

The difference between 2 types can be presented in this example:

When you run the SQL query like ``DROP TABLE table_name``, Spark's going to delete all of data and metadata. While to unmanaged table, Spark only deletes the metadata and the data in the external storages still exists.

