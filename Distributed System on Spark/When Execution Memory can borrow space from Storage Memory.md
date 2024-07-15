Due to nature of _Execution Memory_, you cannot forcefully evict blocks from this pool, because this is the data used in intermediate computations and the process requiring this memory would simply fail if the block it refers to won’t be found

- There is free space available in _Storage Memory_ pool, i.e. cached blocks don’t use all the memory available there. Then it just reduces the _Storage Memory_ pool size, increasing the _Execution Memory_ pool.

- _Storage Memory_ pool size exceeds the initial _Storage Memory_ region size and it has all this space utilized. This situation causes forceful eviction of the blocks from _Storage Memory_ pool, unless it reaches its initial size.
