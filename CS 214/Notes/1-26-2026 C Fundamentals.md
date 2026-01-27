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
		- Note the lower bound: C does not assume 2's complement. In practice, all implementations use 2's complement.
		- `UINT_MAX + 1==0`
		- `INT_MAX + 1` is `undefined`.
		- See also: [[Integer Representations]].
- `char`: 
	- Used to represent characters.
	- Usually 1 byte.
	- Can be `signed` or `unsigned`, this does not matter for ASCII.
	- Technically, `char` is just a smaller `int`.
		- Which is to say that `char x = 100` is the same as `int x = 100`.
		- `'A' + 1 == 'B'`.
		- Note that `char` has smaller bounds.
	- See also: [[Information Storage#Representing Strings|Representing Strings]].
- `float` and `double`:
	- Floating point values.
	- In practice, they follow the single and double precision IEEE floating point.
	- See also: [[Floating Point]].
- C does not have `string` or `bool`:
	- We use an array of `char` instead of a `string`.
	- We use `int` instead of `bool`, where `0` is `false` and `1` is `true`.
```c
if (x == 0)
// same as
if (!x)
```
### Implicit Type Casts
- C automatically inserts conversions between number types as needed.
```c
int x = 1;
long int y = x; // automatic cast from int to long int
double z = y; // automatic cast from long int to double
```
- For operations, C will convert to the "largest" type involved.
```c
int x;
double y;
x + y; // convert x to a double and perform floating-point addition.
int z = x + y; // converts x to a double and the converts the result back to int.
```
- If the operations are of the same type then no such conversion is done.
```c
int a = 5;
double b = a/2;
// b = 2.0
// as a and b are both ints, C does integer division.
```
- The solution:
```c
int a = 5;
double b = (double) a/2; // explicitly cast a to double
// or
double b = a/2.0; // implicitly write 2 as a double.
```
- Casts are treated as operators, so they have a precedence.
`a + b * c == a + (b * c)`
- Can use parenthesis to make it explicit.
```c
((double) a)/2 // definitely correct
(double) (a/2) // probably wrong
```
# Arrays
Arrays are a region a memory that stores a sequence of values. (Thinking of arrays as objects)
We can make array variables in C.
```c
int v[10]; // declares v as an array of 10 ints
// Note: Dimension is written with the name, not the type.
// Note 2: Dimension must be constant.
int u[5], q[6], t; // declares 2 arrays and a regular int.
int m[10][10]; // delcares an array of arrays of ints (10 x 10 matrix).
```
We use brackets for indexing.
```c
v[1] // gets the second element of v
v[0] = 10; // assigns to first element of v
```
Declaring and initializing an array.
```c
int a[3] = {10, 20, 30}; // declares a and initializes its contents.
```
If we are initializing an array, the dimension can remain implicit, we do not need to write it out.
```c
int b[] = {10, 20, 30};
```
We do not need to specify all values in an array when initializing it.
```c
int c[10] = {10, 20, 30};
```
- In C1999 and earlier, the last 7 elements of `c` are uninitialized.
- In c2011 and later, the rest of `c` is initialized to 0.
## Special Syntax for char arrays
```c
char s[] = "Hello";
// creates s as an array of 6 chars and initializes them
char s[] = {'H', 'e', 'l', 'l', 'o', '\0'};
// '\0' is a special char called the terminator (NULL).
```
A string is an array of characters that ends with a terminator.
- Note that the length of the string may not be the length of the array.
	-  You need one extra for the null terminator.
We use terminators to allow arrays to hold strings of various lengths.
```c
char name[255] = "Sample name";
```
# Enums
Enums are fancy integers. They are types with a small set of possible values.
```c
enum direction {up, down, left, right};
```
The above declares a type called "`enum direction`" and four enumerators: up, down, left, right, which are the values of type `enum direction`.
```c
enum direction = {up, down, left, right};
if (a == down) {...}
switch(a) {
	case up: ...
	case down: ...
	case left: ...
	case right: ...
}
```
We can use these to make our code more readable, using `enum` where possible is faster than using, say for example, strings.
- They are more efficient as they are just integers.
- I.E., up, down, left, right are actually, 0, 1, 2, 3.
- Because they are integers, the compiler "helpfully" inserts casts as needed.
```c
int x = up; // same as x = 0
enum direction b = 3; // same as b = right
```
Since they do not provide any type safety, `enum` is mostly used to make code more readable.
# Structs
Like arrays, structs are a way to bundle multiple values together.
- Think objects from Java.
- They are referred to by name and can be different types.
```c
struct point { double x; double y; };
// declares a type "struct point" with two elements, double x and double y.
struct point p;
p.x = 1;
p.y = -2.6;
```
Special syntax for initialization.
```c
struct point p = {1, -2.6};
```
Example:
```c
struct triangle {
	 struct point vertext[3];
	 enum color background;
	 enum color foreground;
	 char name[255];
};
struct triangle my_triangle = {{{0, 0}, {1, 1}, {1, 0}}, blue, red, "special triangle"};
my_triangle.vertex[0].x = 0.5;
if (my_triangle.background == blue){...}
// my_triangle.vertex[0] cannot be null, because it is part of the struct.
```
# Unions
- A struct contains **ALL** of its elements.
- A union contains **ONE** of its elements.
```c
union foo {
	int i;
	double d;
}
union foo x;
// x may contain an int or a double
// x is large enough to store a double
x.i = 1;
// now x contains an int
x.d = 1;
// now x contains a double
// to use the value in the union, you have to know what type is stored there
x.i = 1;
double b = x.d; // technically not defined
// we do not get an error, but we do get a garbage value.
```
Why use unions?
- Back when space was tight, we could use unions to save space when we had variables that were never used at the same time.
- Modern compilers do liveness analysis and automatically combine variables when they can tell it's safe.