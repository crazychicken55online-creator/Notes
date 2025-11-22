- Due to Intel's origin as a 16-bit architecture that was later expanded into a 32-bit one, `word` refers to a 16-bt data type.
	- See also: [[Word Size]].
- As such, 32-bit quantities are called "double words" (2x a normal word).
- Pointers are stored as 8-byte (64-bit) *quad words*, which makes sense as in 64-bit machines the size of an address would be 64-bits, or 8 bytes.
- In x86-64 the `long` data type is implemented with 64 bits.
> [!info] Sizes of C data types in x86-64
> ![[Sizes of C data types in x86-64.png]]
- `gcc` generates assembly code with a single-character suffix denoting the size of the operand.
- E.g., the data movement instruction has 4 variants:
	- `movb` (move byte).
	- `movw` (move word).
	- `movl` (move double word).
	- `movq` (move quad word).
- The suffix 'l' is used for double words, since 32-bit quantities are considered to be "long words".
- The assembly code uses the suffix 'l' to denote a 4-byte (32-bit) integer as well as an 8-byte double-precision floating-point number.
	- Floating-point code involves an entirely different set of instructions and registers.
	- See also: [[Program Encodings]], [[Floating Point]]