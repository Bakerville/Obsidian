These line of codes create temporary view from a dataframe used for **Spark SQL


_Create SparkSession_
```python
from pyspark import SparkSession

spark = SparkSession\
		.builder\
		.appName("Something.com")\
		.getOrCreate()
```
_Read data from file_
```python

df = spark.read.format('.csv')\
		.option('inferSchema','true')\
		.option('header', 'true)\
		.load(file_path)
```

_Create TempView_
```python
df.createOrReplaceTempView(table_name)
```

