- An x86-64 central processing unit (CPU) contains a set of 16 *general purpose registers* storing 64-bit values.
	- These registers are used to store integer data as well as pointers.
- The original 8086 had eight 16-bit registers which all start with `%r` and are suffixed with `%ax` through `%bp`.
- With the extension to [IA32](https://en.wikipedia.org/wiki/IA-32), which is the 32-bit version of the x86 instruction set architecture, designed by Intel, these registers were expanded to 32-bit registers, labeled `%eax` through `%ebp`.
- In the extension x86-64 (the modern 64-bit instruction set architecture), the original eight registers were expanded to 64 bits, labeled `%rax` through `%rbp`.
	- In addition, 8 new registers were added, were labeled `%r8` through `%r15`.
---
- Instructions can operate on data of different sizes stored in the low-order bytes of the 16 registers (least significant bits).
	- Byte-level operations can access the least significant byte (8-bits).
	- 16-bit operations can access the least significant 2 bytes (16-bits).
	- 32-bit operations can access the least significant 4 bytes (32-bits).
	- 64-bit operations can access the least significant 8 bytes, which is the whole register (64-bits).
- When instructions have registers as destinations, two conventions are followed regarding the remaining bytes in the register for instructions that generate less than 8 bytes:
	- Those that generate 1 or 2-byte (8 or 16-bits) leave the remaining bytes unchanged.
	- Those that generate 4-byte quantities set the upper 4 bytes (32-bits) of the register to zero.
---
- Different registers serve different purposes in typical programs, the most unique of them all is the stack pointer `%rsp` which is used to indicate the end position in the run-time stack.
	- Some instructions specifically read and write this register.
- The other 15 registers have more flexibility in their uses.
> [!example] Integer Registers 
> ![[Integer Registers.png]]
*The low-order portions of all 16 registers can be accessed as byte, word (16-bit), double word (32-bit), and quad word (64-bit) quantities.*

---
# Operand Specifiers
- Most instructions have one or more *operands* specifying the source values and the destination location in which to place the resulting operation.
> [!info] Operand Forms
> ![[Operand Forms.png]]
> *Operands can denote immediate (constant) values, register values, or values from memory. The scaling factor `s` must be either 1, 2, 4, or 8.*

- Source values can be given as constants or read from registers or memory.
	- The resulting values can be stored in either registers or memory.
- Therefore the different operand possibilities can be classified into 3 types:
	- **Immediate**: Immediate operands are for constant values. In ATT-format these are written with a "$" followed by an integer using standard C notation.
		- E.g., `$-577` or `$0x1F`.
	- **Register**: Denotes the contents of a register, one of the 16 8-, 4-, 2-, or 1-byte low-order portions o the registers for operands having 64, 32, 16, or 8 bits, respectively.
		- In the above image the notation $r_a$ is used to denote an arbitrary register $a$ and indicate its value with the reference $\text{R}[r_a]$.
			- Here the registers are in an array $\text{R}$ indexed by register identifiers.
	- **Memory Reference**: This operand lets us access some memory location according to a computed address, often called the *effective address*.
		- Since we view the memory as a large array of bytes, we use the notation $\text{M}_b[Addr]$ to denote a reference to the $b$-byte value stored in memory starting at address $Addr$.
- The image above also showed that there are many different *addressing modes* allowing different forms of memory references.
	- The most general form is shown at the bottom: $Imm(r_b,r_i,s)$.
		- This syntax has 4 components: An immediate offset $Imm$, a base register $r_b$, an index register $r_i$ and a scale factor $s$, where $s$ must be 1, 2, 4, or 8. Both the base and the index **must** be 64-bit registers.
		- The effective address is computed as $Imm + \text{R}[r_b]+\text{R}[r_i]*s$.
			- This general form is often seen when referencing elements of arrays
---
# Data Movement Instructions
## Instruction Classes
Instruction classes are a group of instructions that perform the same operation but with different operand sizes.
## The MOV Class
- The MOV class is the simplest data movement instruction, it copies data from a source location to a destination location, without any transformation.
- The class consists for 4 instructions: 
	- `movb`, `movw`, `movl`,`movq`.
	- All 4 instructions have similar effects, they differ primarily in that they operate on data of different sizes: 1, 2, 4, and 8 bytes, respectively.
> [!info] Simple data movement instructions
> ![[MOV Instructions.png]]
- The source operand designates a value that is immediate, stored in a register, or stored in memory.
- The destination operand designates a location that is either a register or a memory address.
- Note that x86-64 imposes the restriction that a move instruction cannot have **both** operands refer to memory locations.
- Copying a value from one memory location to another requires 2 instructions:
	- The first one to load the source value into a register.
	- The second to write this register value to the destination.
> [!example] The 5 possible combinations of source and destination types for MOV
> ![[MOV Instruction Combinations.png]]
> *Recall that the source operand comes first and the destination second.*
- The `movabsq` instruction is for dealing with 64-bit immediate data. The regular `movq` instruction can only have immediate source operands that can be represented as 32-bit [[Integer Representations#Two's Complement Encodings|two's complement numbers]].
	- This value is then sign extended to produce the 64-bit value for the destination.
	- The `movabsq` instruction can have an arbitrary 64-bit immediate value as its source operand and can only have a register as a destination.
- There are 2 classes of data movement instructions when copying a smaller source value to a larger destination.
	- All of these instructions copy data from a source, which can be either a register or stored  in memory to a register destination.
- Instructions in the `MOVZ` class fill out the remaining bytes of the destination with zeroes.
- Instructions in the `MOVS` class fill them out by sign extension.
	- Notice that this is what happens when you type cast from `int` to `long`.
	- See also: [[Integer Representations#Expanding the Bit Representation of a Number|Expanding the Bit Representation of a Number]].
## Data Movement Example
Look at the below example `c` and `assembly` code.
>[!example] C code
>![[Data Movement Example C Code.png]]

> [!example] Assembly Code
> ![[Data Movement Example Assembly Code.png]]

- Tracing the function:
	- When the function begins its execution, parameters `xp` and `y` are stored in registers `%rdi` and `%rsi`, respectively.
	- The next instruction (2) then reads `x` from memory and stores the value in register `%rax`, a direct implementation of the operation `x=*xp` in the C program.
		- Later, `%rax` will be used to return a value from the function, so the return value will be `x`.
	- The next instruction (3) write `y` to the memory location designated by `xp` in register `%rdi`, a direct implementation of the operation `*xp=y`.
- This shows how the `MOV` instructions can be used to read from memory to a register (line 2) and to write from a register to memory (line 3).
- Note that "pointers" in C are simple addresses.
	- Dereferencing a pointer involves copying that pointer to a register and then using this register in a memory reference.
- Also note that local variables (like `x`) are often kept in registers rather than stored in memory locations.
	- This is because register access is much faster than memory access.
---
# Pushing and Popping Stack Data
- A stack is a LIFO (Last in First Out) data structure.
