b### Map phase

- During the map phase, each executor writes its output data for a given shuffle partition to local disk storage instead of sending it directly to the reducer.
- The intermediate data is written as individual spill files, typically in a round-robin manner across multiple local disks to distribute the I/O load.
- If the data for a single shuffle partition exceeds the executor's memory limit, i**t will be spilled to disk in multiple spill files**.

### Reduce Phase

- The reduce tasks fetch the spilled data partitions from the map tasks' local disks, bringing them into memory for processing.
    
- The reduce tasks operate on the merged data, performing the necessary computations

