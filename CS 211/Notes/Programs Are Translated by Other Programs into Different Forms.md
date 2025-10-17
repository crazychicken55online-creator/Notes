If we were to look at a typical hello world program in C, you'll notice that it is actually a high-level C program, high-level as it as enough abstractions to make the code human readable.
```c title=hello.c
#include <stdio.h>
int main() {
	printf("hello,world\n");
	return 0; 
}
```
However, in order to run the C program, `hello.c` the system needs to translate each C statement into a sequence of low-level machine language instructions (Note that your system can only understand 0s and 1s, binary code). 
These instructions are packaged into a form called executable object program and stored as a binary disk file.
Objects programs are also referred to as executable object files.
On a Unix system, the translation from source file to object file is performed by a compiler driver.
To visualize this, the below image shows what happens when you run:
```terminal
gcc -o hello hello.c
```
![[Program Translation Pipeline.png]]
Here, the **GCC compiler driver** reads the source file `hello.c` and translates it into an executable object file `hello`. The translation is performed in the sequence of four phases (as seen in the image). The programs that perform the 4 phases are called the preprocessor, compiler, assembler, and linker; together they are called the compilation system.
## Preprocessing Phase
![[Preprocessing Phase]]
## Compilation Phase
![[Compilation Phase]]
## Assembly Phase
![[Assembly Phase]]
## Linking Phase
![[Linking Phase]]
