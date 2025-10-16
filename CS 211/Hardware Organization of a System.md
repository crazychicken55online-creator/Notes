Below is diagram of the hardware organization of a typical system:
![[Hardware Organization of a Typical System.png]]
To understand how the `hello.c` example works we need to understand how the hardware it runs on is organized.
# Buses
- Buses transport information around the system, they are electrical conduits that run throughout the system and carry bytes of information back and forth between the components.
- Buses are usually designed to transfer fixed-sized chunks of bytes known as **words**.
- The number of bytes is a fundamental system parameter (the bus is designed to transport that amount, it can't be changed).
- Most machines today have either 4 bytes (32 bits) or 8 bytes (64 bits) word sizes.
# I/O Devices
- I/O Devices (Input/Output Devices) are the system's connection to the real world, it is how it reads input (think keyboard, microphone, touchscreen, etc.) and gives an output (monitor, speaker, etc.).
- Our example system (from the diagram above) has 4 I/O devices: a keyboard and a mouse for user input, a display for user input, and a disk drive (or simply disk) for long-term storage of data and programs.
- Each I/O device is connected to the I/O bus by either a **controller** or an **adapter**.
	- Controllers are chip sets in the device itself or on the system's main printed circuit board (motherboard).
	- Adapters are cards that plug into a slot on the motherboard.
	- They both serve the same purpose of transferring information back and forth between the I/O bus and I/O devices.
# Main Memory
- Main memory is a temporary storage device that holds both the program and the data it manipulates while the processor is executing the program.
- Main memory consists of a collection of **dynamic random access memory (DRAM)** chips.
- The memory is organized as a linear array of bytes, each with its own address (array index) starting at 0.
# Processor
- Also known as the **Central Processing Unit (CPU)** interprets (executes) instructions stored in main memory.
- At the core of the CPU is a word-size storage device (register) called the **program counter (PC)**.
- At any point in time the PC points at (contains the address of) some machine-language instruction in main memory.
- A processor operates according to a very simple instruction execution model, which is defined by its **instruction set architecture**.
	- In the above model, instructions execute in a strict sequence, and executing those instructions requires a series of steps.
		- The processor reads the instruction from memory pointed at by the program counter (PC), interprets the bits in the instruction, performs some simple operation dictated by the instruction, and the updates the PC to point to the next instruction.
			- The next instruction may or may not be contiguous in memory to the instruction that was just executed. (Executed in a first come first serve basis, the processor does not care about what it is executing, it just executes what the program counter (PC) tells it to execute).
	- There are only a few of these instructions, which revolve around the main memory, the register file, and the arithmetic/logic unit (ALU).
		- The **register file** is a small storage device that consists of a collection of word-size registers, each with its own unique name. 
		- The **ALU** computes new data and address values.
	- Here are a few simple operations that the CPU may carry out at the request of an instruction:
		- **Load**: Copy a byte or a word from main memory into a register, overwriting the previous contents of the register.
		- **Store**: Copy a byte or a word from a register to a location in main memory, overwriting the previous contents of that location.
		- **Operate**: Copy the contents of two registers to the ALU, perform an arithmetic operation on the two words, and store the result in a register, overwriting the previous contents of that register.
		- **Jump**: Extract a word from the instruction set itself and copy that word into the program counter (PC), overwriting the previous value of the PC.
	- We can distinguish the processor's instruction set architecture from its **microarchitecture**.
