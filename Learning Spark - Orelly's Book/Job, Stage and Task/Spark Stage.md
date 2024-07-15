Stages are created based on what operations can be performed serially or in parallel. Not all Spark operations can be performed in a single stage, so they may be divided into multiple stages. Often stages are delineated on the operator's computation boundaries, where they dictate data transfer among Spark executors.

![[Spark Stage.png]]
[[Spark Application and SparkSession]]

[[Spark Job]]

