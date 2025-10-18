- The main idea behind virtual memory is giving every program the illusion that they have unlimited memory, more specifically, virtual memory gives every program has its own private view of the system’s memory address space.
- Since every process has its own virtual address space, it is impossible for one program to accidentally or maliciously access memory used by another program.
	- If a program tries to access memory it doesn't own, the OS steps in and stops it, protecting all other processes and preventing the system from crashing.
	- This is why you will see programs crash if they access memory they do not own, the OS steps in and kills it.
> [!example] Virtual Address Space of a Process (regions not to scale)
> ![[Virtual Address Space.png|500]]
