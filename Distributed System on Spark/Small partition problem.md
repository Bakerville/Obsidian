When data is processed from disk to storage. Data on disk is arranged in chunks or contiguous fule blocks

The size of a partition in Spark is managed by _spark.sql.files.maxPatitionBytes_

The small partition problem occurs when this size set too small and the number of partition grow too much. Many small patition files, introducing an inordinate amount of disk I/O and performance degration thanks to filesystem operations such as opening, closing, and listing directories. which on a distributed file system can be slow.

