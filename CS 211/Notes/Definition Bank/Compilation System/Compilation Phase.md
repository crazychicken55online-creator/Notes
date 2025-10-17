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