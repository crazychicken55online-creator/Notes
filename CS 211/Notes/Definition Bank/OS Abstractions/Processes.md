- The operating system's (OS) abstraction for running a program.
- A process includes not just the machine code (in, say, the `hello.c` file) it also includes the data the code is working with, the memory it's using, the registers which is holding temporary values (for caching purposes), and a "bookmark" of the instruction it is currently on, which is in the [[Program Counter|program counter (PC)]].
- A process is running and instance of the program.
# Context Switching
- Note that context switching is facilitated by the [[Kernel|kernel]].
- The OS acts a manager, letting a program (like the `hello.c` program) run for a fraction of a second, then it decides to pause `hello.c` and run something else (like say Spotify) for a fraction of a second.
	- This act of swap is done thousands of times per second and gives you an illusion that all programs on your computer are running at the same time.
- The act of swapping processes on the CPU is called a context switch, and it has multiple steps.
	1. Save context: The OS "pauses" your `hello` process. It saves its entire context, the values in all the registers, the program counter (bookmark), into main memory.
	2. Load context: The OS then loads the saved context of the next process (e.g., Spotify) from memory into the CPU's registers and program counter.
	3. Resume: The OS tells the CPU to resume. The CPU, which is now loaded with the new program's context, continues running the program exactly where it had left off, the program does not perceive a pause.
> [!example] Context Switching Visualization
> ![[Context Switching Visualization.png]]
