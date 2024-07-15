This Join strategy is used when joining two datasets, one small (fitting in the driver's and executor's  memory) and another large enough to be spared from movement, need to be joined over certain conditions or columns. 

Using a Spark broadcast variable, the smaller dataset is broadcasted by the driver to all Spark executors, and subsequently joined with the larger dataset on each executor.

![[Broadcast Join.png]]


By default, Spark uses broadcast join if the smaller dataset is less than 10MB. This value is controled by `spark.sql.autoBroadcastJoinThreshold`

This type of joins is the easiest and fastest in Spark, since it avoids all shuffles. Use this type under the following conditions for maximum benefit:

- ***When each key within the smaller and larger datasets is hashed to the same partition by Spark ***

- ***When one dataset is much smalller than the other (default is 120MB, can set more)***

- ***When you only want to perform an equi-join, to combine two datasets based on mathching unsorted keys***

- ***When you are not worried  by excessive network bandwidth usage or Out of Memory errors, because the smaller dataset will be broadcast to all Spark executors
