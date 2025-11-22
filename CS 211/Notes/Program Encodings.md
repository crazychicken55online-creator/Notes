# The Compilation Chain
The `gcc` compiler driver coordinates a sequence of programs that turn c source code into an executable file.
- See also: [[Programs Are Translated by Other Programs into Different Forms]].
# Machine-Level Code Basics
- All programs, including C programs, are just a long sequence of bytes to the CPU. 
- It involves many "programmer-visible states" that the C code hides:
- The [[Program Counter|program counter (PC)]]: In x86-64 machines the program counter is in the 64-bit `%rip` register. It holds the memory address for the next instruction to be executed.
- The Register File: A set of 16 general-purpose 64-bit registers. These are small and fast storage locations used to hold data and pointers.
- Condition codes: Single-bit flags (e.g., `ZF` for Zero Flag, `SF` for Sign Flag) that store status information about the result of the most recent arithmetic or logical operation.
	- See also: [[Operations in Boolean Algebra]], [[Shift Operations]].
- Vector Registers: Used for floating-point data and Single Instruction Multiple data (SIMD) operations.