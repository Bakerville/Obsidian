Shuffle partitions are created during the shuffle stage. By default, the number of shuffle partition is set to 200 in spark.sql.shuffle.partitions. You can adjust this number depending on the size of dataset

>[!note]
>The default value for _spark.sql.shuffle.partitions_ is too high for smaller or streaming workloads; you may want to reduce it to a lower value such as the number of cores on executors or less
>- **Remember that**, the parameter _spark.sql.shuffle.partitions_ is number of partitions when shuffle occurs. if its value is 200, the number of shuffle partition is 200, no matter the size of data or [[Partition]] of data
>- It is different to _spark.sql.files.maxPartitionBytes_, which can only determine the number of [[Partition]] on reading a file.

Shuffle consume both network and disk I/O resources. During these operations, the shuffle will spill results to executors's local disks at the location specified in _spark.local.directory_

