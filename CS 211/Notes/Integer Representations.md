- Integers can be represented in two ways in order to represent negative/positive signed/unsigned integers.
# Integral Data Types
- Integral data types are those data types which represent a finite range of integers.
- Each type can specify a size with keyword `char`, `short`, `long`, as well as whether the values are all nonnegative (`unsigned`) or possible negative (we do not have a `signed` as that is the default, so there is no keyword needed).
> [!example] Typical Ranges for C integral data types for 64-bit programs.
>  ![[Typical ranges in C for integral data types in 64-bit programs.png|500]]

# Unsigned Encodings
## Binary to Unsigned $B2U_w$
For vector $\vec{x}=[x_{w-1},x_{w-2},...,x_0]$:
$$B2U_w(\vec{x})\doteq \sum_{w-1}^{i=0}x_i2^i$$
In the above equation $\doteq$ means that the left-hand side is defined to be equal to the right hand side.
An example of the equation in action:
$$B2U_w([0001])=0*2^3+0*2^2+0*2^1+1*2^0=0+0+0+1=1$$
It is basically converting binary to decimal, however it should be noted that this only works for unsigned integers, signed integers (which could be negative) do not easily convert in this way.





