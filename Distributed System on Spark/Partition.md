Related Topic: [[How Spark distributes tasks to Executors]]


All data you work with in Spark is split into partitions. What is in single partitions?

Partition size completely depends on the data source you use. By default each input split returned by InputFormat is mapped to a single partition in RDD. For most of the files on HDFS single input split is generated for a single block of data stored on HDFS, which equals to approximately 64MB of 128MB of data. Approximately, because the data in HDFS is split on exact block boundaries in bytes, but when it is processed it is split on the record splits. For text file the splitting character is the newline char, for sequence file it is the block end and so on. The only exception of this rule is compressed files – if you have the whole text file compressed, then it cannot be split into records and the whole file would become a single input split and thus a single partition in Spark and you have to manually repartition it.


>[!note]
> - A partition is the way Spark arranges the data from storage
> - A single thread running on a single core can work on a single partition
> - The default size of a partition is 128MB, set this value too small can cause [[Small partition problem]]






