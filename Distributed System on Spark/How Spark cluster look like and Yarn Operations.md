![[Driver and Worker.png]]

When you have a YARN cluster, it has a YARN Resource Manager deamon that controls the cluster resources and a series of YARN Node Managers running on the cluster nodes and controlling node resource utilization. From the YARN standpoint, each node represents a pool of RAM that you have a control over. When you request some resources from YARN Resource Manager, it gives you information of which Node Managers you can contact to bring up the execution containers for you. Each execution container is a JVM with requested heap size. JVM locations are chosen by the YARN Resource Manager and you have no control over it – if the node has 64GB of RAM controlled by YARN (_yarn.nodemanager.resource.memory-mb_ setting in yarn-site.xml) and you request 10 executors with 4GB each, all of them can be easily started on a single YARN node even if you have a big cluster.

When you start Spark cluster on top of YARN, you specify the amount of executors you need (_–num-executors_ flag or _spark.executor.instances_ parameter), amount of memory to be used for each of the executors (_–executor-memory_ flag or _spark.executor.memory_  parameter), amount of cores allowed to use for each executors (_–executor-cores_ flag of _spark.executor.cores_ parameter), and amount of cores dedicated for each task’s execution (_spark.task.cpus_ parameter). Also you specify the amount of memory to be used by the driver application (_–driver-memory_ flag or _spark.driver.memory_ parameter).

Ref: (https://0x0fff.com/spark-architecture/)


[[What is Heap on Java Virtual Machine]]



