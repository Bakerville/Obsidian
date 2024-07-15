Each stage consists of one or many Spark tasks (a unit of execution), which are then federated across each Spark executor; each task maps to a single core and works on a single partition. Examples, an executor with 16 cores can have 16 or more tasks working on 16 or more partitons in parallel

[[Spark Application and SparkSession]]

[[Spark Stage]]
