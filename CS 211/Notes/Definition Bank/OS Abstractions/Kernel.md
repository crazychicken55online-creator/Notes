Also known as Operating System Kernel.
- The kernel is a portion of the operating system (OS) code that is always in memory.
	- Note that the kernel is **not** a separate process. Instead, it is a collection of code and data structures that the system uses to manage all the processes.
- When a program requires some action by the operating system, such as reading or writing a file, it executes a special **system call** instruction, which transfers control over to the kernel.
	- The kernel then performs the requested operation and returns back to the program.