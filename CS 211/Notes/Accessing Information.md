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