Transformations are used to  transform one DataFrame into a new one (DataFrame is immutable) 

## 1. Narrow Dependency Transformation

A transformation performed independently on a single partition to produce valid results.

For example, the <code>where()</code> clause transformation is a narrow transformation. Spark executor should be able to perform this filtering on each partition. They not depend on  any other partition.

![[Narrow Dependency Transformation.png]]

## 2. Wide Dependency Transformation

The transformation that requires data from other partitions to produce valid results

For Example, The **<code>groupBy()</code>** can produce a new DataFrame on each partition. But, you want to compute the sum of each partition. If you count on each partition and combine them, you can not get invalid result.

![[Wrong Wide Dependency Transformation.png]]

In the right way, it needs a shuffle/exchange stage. Spark put these row in same group into same partition. Then the aggregation is applied on each partition. Finally, the result is combined with all of them.

![[Right Wide Transformtion.png]]

[[What is Shuffle on Spark]]
