
When you use a transformation, to compute the total for each group (like using **GROUP BY** and **SUM** in SQL), the shuffle might happen. Why the shuffle is essential in some cases?

Imagine, for each key you need to get the sum of all values. But in Spark, the value in same group is located in many different workers. Shuffle gets the value having the same keys into the same virtual machine. That is also known as  **Wide Dependency Transformation** (can see this definition on [[Transformation and Shuffle]])

In the shuffle operation, the task that emits the data in the source executor is **mapper**, the task that consumes the data into the target executor is **reducer**, and what happen between them is **shuffle**.

Shuffling in general has 2 important compression parameters: **_spark.shuffle.compress_** – whether the engine would compress shuffle outputs or not, and **_spark.shuffle.spill.compress_** – whether to compress intermediate shuffle spill files or not. Both have the value “true” by default, and both would use **_spark.io.compression.codec_** codec for compressing the data, which is [snappy](https://en.wikipedia.org/wiki/Snappy_(software)) by default.


 