These cases under following conditions should use [[Shuffle Sort Merge Join]]:

- When each key within 2 large datasets can be sorted and hashed into the same partitions in Spark

- When you want to perform only equi-joins to combine 2 datasets based on matching sorted data

- When to prevent ``Exchange`` and ``Sort`` to save large shuffles across the network

