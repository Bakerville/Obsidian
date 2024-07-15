`MEMORY_ONLY`: Data is stored directly as objects and stored only in memory. This provides fast access to the data but consumes more memory.

`MEMORY_ONLY_SER`: Data is serialized as compact byte array representation and stored only in memory. To use it, it has to be deserialized\

`MEMORY_AND_DISK`: Data is stored directly as objects in memory

`DISK_ONLY`: Data is serialized and stored on disk

`OFF_HEAP`: Data is stored off-heap. Off-heap memory is used in Spark for storage and query execution

`MEMORY_AND_DISK_SER`: Like `MEMORY_AND_DISK`, but data is serialized when stored in memory (Data us always serialized when stored on disk).


