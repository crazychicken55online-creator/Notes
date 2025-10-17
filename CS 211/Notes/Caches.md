# Reason for Cache
- Caches are needed for optimization since executing a program takes multiple, repetitive, steps.
	- When a processor runs a program it must first copy the program over into [[Main Memory|main memory]] and then its copied from main memory to the display device.
- The idea behind caching is that the system can get the effect of both very large memory **and** very fast memory by exploiting [[Locality|locality]].
# Larger devices are slower than smaller devices
- The disk drive on a system might be 1,000 times larger than the main memory, but it might take the processor 10,000,000 times longer to retrieve data from the disk compared to the main memory.
	- Similarly, processors can retrieve data from register files many times faster than main memory, however, a typical register file only stores a couple hundred bytes of information.
# Cache Memories
![[Cache Memories.png]]
- To deal with the processor-memory gap, the system includes a L1 and L2 cache, these are smaller devices, that, together, are known as cache memories.
	- # L1 Cache
		- An L1 cache on the processor chip holds tens of thousands of bytes and can be accessed nearly as fast as a register file.
	- # L2 Cache
		- An L2 cache is a larger cache that can hold thousands to millions of bytes and is connected to the processor by a special memory bus (note that it in **not** on the processor like the L1 chip).
		- It might take 5-10 times longer for the processor to access the data in L1 cache, however, this is still 5-10 times faster than main memory.
	- L1 and L2 caches are implemented with hardware technology known as **static random access memory** (**SRAM**).
		- Newer and more powerful systems even incorporate a 3rd cache called L3 cache.
- Cache memories serve as temporary storage for information the processor is likely to need in the near future.
# Memory Hierarchy Visualization
![[Memory Hierarchy.png]]
- Key idea is that memory hierarchy at one level counts as cache for the next level (L1 is the cache for L2 which the is cache for L3 which is the cache of main memory and so on).