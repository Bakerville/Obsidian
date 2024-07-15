During map and shuffle operations, Spark writes to and reads from local disk's shuffle files, so there is heavy I/O activity. This can result in a bottleneck, because the default configurations are suboptimal for large-scale Spark jobs.

We capture a few recommended configurations to adjust so that the map, spill, and merge processes during these operations are not encumbered by
inefficient I/O and to enable these operations to employ buffer memory before writing the final shuffle partitions to disk. Tuning the shuffle service running

![[screenshot-1720256401581.png]]

