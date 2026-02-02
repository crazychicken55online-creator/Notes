# Dynamic Memory
- Ways in which we can create memory objects:
	- Declare variables.
	- String literals.
	- Functions.
- All of these need to be specified (number and size) at compile time.
- What if we need to create objects at run-time?
	- If we do not know the length of the array in advance.
	- If we do not know how many linked list nodes to create.
- In C, we use `malloc()` to allocate memory.
```c
void* malloc(size_t length);
```
- `size_t` is an unsigned integer type (usually `unsigned long`).
- `void*` is an "untyped" pointer.
	- Cannot be dereferenced.
	- Can be compared for equality (e.g., to `NULL`).
	- Automatically casts to any pointer type.
```c
int *array = malloc(sizeof(int)*number_of_items);
// could cast it too
int *array = (int*)malloc(sizeof(int)*number_of_items);
```
- Dynamically allocated `malloc()` or `calloc()` objects are made on the heap.