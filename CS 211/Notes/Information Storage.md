- A single byte consists of 8 bits. In binary notation, its values range from $00000000_2$ to $11111111_2$. When viewed a decimal integer, its values range from $0_{10}$ to $255_{10}$.
	- Binary notation is too verbose, while decimal notation is too tedious to convert back and forth from.
- As a fix for this, we write bit patterns as base-16, or hexadecimal numbers.
# Hexadecimal Notation
![[Hexadecimal Notation]]

# Data Sizes
- For a machine with w-bit [[Word Size|word size]], the virtual addresses can range from $0$ to $2^w - 1$, giving the program access to at most $2^w$ bytes.
> [!example] Typical sizes (in bytes) of basic C data types
 ![[Bytes of C data types.png|500]]

- With the exception of `char` all data types in C are assumed to be signed unless otherwise declared.
- Addition C allows for a variety of ways to order the keywords and to include or omit optional keywords.
	- E.g., `unsigned long`, `unsigned long int`, `long unsigned`, `long unsigned int` all have identical meaning. However the forms in the image above are considered to be most standard.
# Addressing and Byte Ordering
- In almost all machines multi-byte objects are stored contiguous in memory.
	- It should be noted that structs pad themselves such that they end up taking up space that is divisible by 4.
		- E.g., If a struct has an `int` and a `char`, assuming that an `int` takes up 4 bytes and a `char` takes up 1 byte, instead of the struct taking up 5 bytes, it will take up 8, as it will pad the `char` such that the `int` starts at an address divisible by 4.
			- It will be like so: `char` (1 bytes), padding (3 bytes), `int` (4 bytes), therefore taking up 1+3+5 = 8 bytes.
	- For example if a variable `x` of type `int` (let's assume 4 bytes) has an address 0x100. Which is to say that if you were to do `&x` you'll get 0x100. The 4 bytes of x then would be 0x100, 0x101, 0x102, and 0x103. 
- # Little Endian and Big Endian
	- For ordering the bytes representing an object, there are two common conventions, little endian and big endian.
	- Little endian has the **least significant byte** (smallest part) stored first (at the lowest memory address).
		- E.g., The number 0x12345678 is stored as 78 56 34 12
	- Big endian has the **most significant byte** (largest part) stored first (at the lowest memory address).
		- E.g., The number 0x12345678 is stored as 12 34 56 78
	- Note on significance:
		- Significance refers to how much a digit impacts the overall value of a number.
			- E.g., In decimal if we were to take the number $1234_{10}$, 1 would be the most significant digit as it represents 1,000 and 4 would be the least significant digit as it represents 4.
			- For bytes, if we had a hexadecimal number 0x78281290, here 0x78 is the most significant byte as it affects the overall number the most, and 0x90 is the least significant byte as it impacts the overall number the least.
			- See also: [[Hexadecimal Notation]].
# Representing Strings
- A string in C is represented by an array of characters terminated by null (a 0 byte). Each character is represented by their ASCII character code.
> [!example] ASCII Table
![[ASCII Table.png]]

- Using the ASCII table, if we want to represent "hello" in binary, it would be 01101000 01100101 01101100 01101100 01101111. In hexadecimal, it would be 0x68656C6C6F.
# Introduction to Boolean Algebra
- The binary values 1 and 0 represent true and false.
- 