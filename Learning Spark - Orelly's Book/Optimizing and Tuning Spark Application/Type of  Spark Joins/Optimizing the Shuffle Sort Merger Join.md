Before topic: [[Shuffle Sort Merge Join]]

We can eliminate the ``Exchange`` step from this scheme if we create partitioned buckets for common sorted keys or columns on which we want to perform frequent equi-joins. 

This picture presents the Spark plan before bucketing:

![[Pasted image 20240703101700.png]]


But when put a line of code before Join

```python
dataframe.repartition(number_partition, attribute)
```

The plan will change, and have less cost. This is an example:

![[Pasted image 20240703102038.png]]

There are not any ``Exchange``. Because, we repartitioned and sorted tables. As such, there's no need to sort during the [[Shuffle Sort Merge Join]].  Right in above picture, Spark skipped the ``Exchange``, go straight to ``WholeStageCodeGen``.

