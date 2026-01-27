https://groupme.com/join_group/112640376/yNpoIHe7
# Variables
```c
int x; // declares a variable.
```
- `x` represents a location in memory large enough to store an `int`.
- Note: `x` represents a location, not a specific value.
	- Meaning that we can store different `int` values in `x` over its lifetime.
	- `x` has a location we can obtain (pointer dereferencing).
```c
&x // address of x; evaluates to a pointer that points to x in memory.
```
Note that variables are not initialized by default, (except global variables).
Inside a function, variables have no value until a variable is declared within the function (scope).
- "Indeterminate"/"Random" (Sort of).
Initialize a variable when declaring it.
```c
int n = 0;
```
- Initialization is simply assigning the value after it is declared, you can do both in the same line.
Assigning a variable after declaring it:
```c
int n;
// dont use n here (has no value)
n = 1;
```
## Basic Types
When we declare a variable, we must give it a type.
- The type says how much space to reserve for the variable.
- It also guides the translation of some operations (e.g., Integer vs. Floating point arithmetic).
### Specific types
- Different types of int:
	- 3 sizes: Regular, Short, and Long.
	- For regular, just write `int`.
	- For the others, write the size or size `int`.
	- 2 "signed-nesses": signed (default) and unsigned.
	- `unsigned int`
	- `unsigned long int`
	- `unsigned long` (same as `unsigned long int`).
	- `int`
	- `signed int` (same as `int`).
- C does not require specific sizes for these, except:
	- `short int` is at least 2 bytes.
	- `long int` is longer than a `short int`.
	- `int` is at least as long as a `short int`.
	- `int` is no longer than a `long int`.
- On our hardware (iLab):
	- `short int`: 2 bytes
	- `int`: 4 bytes
	- `long int`: 8 bytes
- Traditionally, "regular" `int`s were register length, for speed but in 64-bit architectures, we felt that was wasteful, so that is no longer the case.
- By default, `int`s can represent positive and negative numbers (and zero), `unsigned int`s cannot have negative values.
	- Often, we do not want to have negative values.
	- We can use the bit representations for negative numbers to represent larger positive numbers, justifying the existence of `unsigned int`.
	- E.g., Range of 32-bit integers:
		- `unsigned`: $0\dots 2^{32}-1$
		- `signed`: $-(2^{31}-1)\dots 2^{31}-1$
