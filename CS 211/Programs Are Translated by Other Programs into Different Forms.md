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
The preprocessor (`cpp`) modifies the original C program according to directives that being with `#`. Such as `#include <stdio.h>` in line 1 of `hello.c` tells the preprocessor to read the contents of the system header file `stdio.h` and insert it directly into the program text. The result of this is `hello.i`
## Compilation Phase
The compiler (`cc1`) translates the text file `hello.i` into the text file `hello.s` which an contains assembly-language program. This program includes the below definition of main:
```asm title=hello.s
main:
  subq $8, %rsp
  movl $.LC0, %edi
  call puts
  movl $0, %eax
  addq $8, %rsp
  ret
```
Each of lines 2–7 in this definition describes one low-level machine language instruction in a textual form. Assembly language is useful because it provides a common output language for different compilers for different high-level languages.
## Assembly Phase
The assembler (`as`) translates `hello.s` into machine-language instructions and then packages them in a form known as a relocatable object program, and stores the result in `hello.o`. The file is a binary file with 17 bytes to encode the instructions of main. Viewing `hello.o` with a text editor would result in gibberish.
## Linking Phase
The linker (`ld`) handles the merging of the `printf` function from the standard C library with our `hello.o` program. The result is a `hello` file, which is an executable object file (or simply an executable) that is ready to use.
