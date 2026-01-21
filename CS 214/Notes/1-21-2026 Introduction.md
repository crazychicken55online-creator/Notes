# What is systems programming?
- This course will look at the lower-level software portions of your computer/programming environment.
	- Language run-time system.
	- Operating System (OS) services.
		- The OS provides abstractions over hardware.
		- See also: [[The OS manages the Hardware]]
		- It provides protection from other programs and users.
		- It provides common implementation of useful features.
		- It provides a basic user interface.
	- This course will look at low-level interfaces that programs use to communicate with the OS.
## Why Linux/POSIX?
- On all the iLab machines and easily accessible and properly documented.
	- Also free.
## Why C?
- Very closely connected to Unix/Linux/POSIX.
	- C was created to write Unix in.
- C provides low-level access to OS features.
	- It is a "portable assembly language."
	- Note that C is a high level language technically as it is not assembly.
- C puts very few barriers between programmers and the hardware.
	- Very hands off, lets you do what you want.
- Most modern languages are inspired by C syntax, so it is familiar to most.
### How is C different from Java?
- C and Java are similar in many ways.
- Java is an object oriented programming language (OOP) whereas C is a declarative language.
	- C has no struct attached methods.
```bash
gcc -Wall -std=c99 -fsanitize foo.c -o foo
```
- C compiles code directly to machine language (executable files).
	- There is no virtual machine.
		- Like the Java Virtual Machine (JVM).
	- The C compiler used in this course, and on the iLab machines is gcc.
		- The compiler translates source code to other code (usually machine code).
		- `gcc <source file>`: compiles and links an executable named a.out.
		- `gcc <source file> -o <output file>`: compiles and links an executable named `<output file>`
		- `gcc -c <source file>`: compiles to an "object file" (.0).
		- `gcc <object files...> -o <executable name>`: links one or more compiled object files to an executable program.
	- Other recommended options:
		- `-std=c99`: requests the 1999 standard for C.
		- `-g`: include information for debuggers.
		- `-Wall`: enable compiler warnings.
		- `-fsanitize=address`: enabled AddressSantizer (run-time memory checks).
		- `-fsanitize=undefined`: enable UBSan (checks for undefined behavior).
- See also: [[Programs Are Translated by Other Programs into Different Forms]]
