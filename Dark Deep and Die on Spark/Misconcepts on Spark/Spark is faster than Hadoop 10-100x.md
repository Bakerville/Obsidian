This statement is based on a benchmark statistics on Apache Spark website. But only compare the efficience of 2 systems with bench mark is not pretty meaningful (this tests can be runned in tricky way).

In general, Spark is faster than MapReduce because of:

1. Faster task startup time. Spark forks the thread, MR brings up a new JVM
2. Faster shuffles. Spark puts the data on HDDs only once during shuffles, MR do it 2 times
3. Faster workflows. Typical MR workflow is a series of MR jobs, each of which persists data to HDFS between iterations. Spark supports DAGs and pipelining, which allows it to execute complex workflows without intermediate data materialization (unless you need to **shuffle** it)
4. Caching. It is doubtful because at the moment HDFS can also utilize the cache, but in general Spark cache is quite good, especially its SparkSQL part that caches the data in optimized column-oriented form

All of these gives Spark good performance boost compared to Hadoop, which can really be up to 100x for short-running jobs, but for real production workloads it won’t exceed 2.5x – 3x at most.