## Type modifiers, qualifiers, and attributes are bound to the left.
```C
char* name;
```
Where `char*` is the type and `name` is the identifier.
If we were to use qualifiers and attributes it would look like this (still left bound):
```C
char const* const path_name[[deprecated]];
```
Where the first `const` qualifies the `char` to its left, the `*` makes it a pointer, and the second `const` again qualifies what is to its left. The attribute `[[depcreated]]` clearly attaches to the identifier `path_name`.
More notably in this particular example:
- `path_name` is the name of the variable.
- `[[depcreated]]` is a C++ attribute that tells the compiler (and programmers) that the variable `path_name` is outdated and should no longer be used. If this variable is used, the compiler will shoot out a warning.
- `const path_name`: The `const` keyword modifies what is to its left. Here, it modifies the pointer itself, which means that `path_name` is a **constant** pointer.
- The `*` means that `path_name` is a pointer. It holds a memory address rather than a value directly.
- `char const` describes the type of data that the pointer points to. `char const` is the same as `const char` and it means that the pointer points to a character which is **constant**.
	- This means that you *cannot* use this pointer to modify the character data it points to.
## Other things to note:
### We do not use continued declarations as they obfuscate the bindings of type declarators.
```C
unsigned const*const a, b;
```
Here `b` has type `unsigned const` which is to say that the first `const` goes to the type, and the second `const` only goes to the declaration of `a` and **not** `b`. These rules are confusing so there's no point in bothering with them.
### We use array notation for pointer parameters
