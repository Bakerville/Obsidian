Firstly, the memory of an executor in Spark is manged by _spark.executor.memory_. This is divided into 3 sections of memory:
_execution memory_, _storage memory_, and _reserved memory_


![[Pasted image 20240705085408.png]]


So, what are the purposes of these memory sections?

1. **Reserved Memory**: This is the memory reserved by the system and its size is hardcoded. As of Spark 1.6.0, it values 300MB, which means that 300MB of RAM do not participate in Spark memory region size for caculations. Remember that this memory is called "reserved", in fact it is not used by Spark anyway, but it sets the limit of memory which users can allocate.

2. **Spark Memory**: this is the memory managed by Apache Spark. Its size can be caculated by _(Java Heap - Reserved Memory)* spark.memory.fraction_ (in 1.6.0, it is _(Java Heap -300)*0.75_). For Example, with 4GB heap this pool would be 2847MB in size. This pool includes 2 regions - [[Storage Memory]] and [[Excution Memory]], this fraction is set by _spark.memory.storageFraction_ parameter, which defaults to 0.5. When the memory pressure occurs, this boundary would be moved.
	
	


	
