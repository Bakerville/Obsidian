
When you execute something on a cluster, the processing of your job is split up into stages, and each stages is split into tasks

You can consider each JVM as an executors  as a pool of task executions slots. Each Executors give you  _spark.executor.cores_ / _spark.task.cpus_ execution slots for execute tasks,  with a total of _spark.executor.instances_ executors. 

**Example:**
When you get:
- 12 nodes in YARN Cluster Manager
- 64GB RAM/node
- 32 CPU cores/node

With this configuration, you starts 2 executors with 26GB RAM for each (not full, spend some RAM for system processes, YARN Node Manager and DataNode), each executor with 12 cores to be utilized. So, in total, your cluster can handle _12 machines_ x _2 executors per machine_ x _12 cores per executor_ (1 core deal with 1 task) = 288 task slots. This means that your Spark cluster can run up to 288 tasks in parallel. The amount of RAM you can use for caching your data on this cluster is 0.9 _spark.storage.safetyFraction_ * 0.6 _spark.storage.memoryFraction_ * 12 machines * 2 executors per machine * 26 GB per executor = 336.96 GB.

[[How Spark cluster look like and Yarn Operations]]

