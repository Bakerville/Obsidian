_cache()_ will store as many of the partitions read in memory across Spark excutors as memory allows.

Example, you get 12-partiton-Dataframe , but only 4.5 partitions can fit in memory, only 4 will be cached. 

Since all of your data is not cached, when you wanna access data again, the patitions that are not cached will be recomputed, slowing down Spark jobs.

Python code

```python
df = spark.range(1,100000,12).toDF("id")
df.cache()
df.count()
```
The next runs from the first are  12 times faster becauser you cached all of 12 partitions of the `df` DataFrame.

![[Spark Caching 12 partitions.png]]


>[!note]
>When you use `cache()` or `persist()`, the DataFrame is not fully cached until you run an action that goes through every record (as `count()`). If you use `show()`, only the 20 first rows are cached. Because Catalyst Optimizer no need to compute all partitions.
              



