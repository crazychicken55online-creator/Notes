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
- The greatest value one can hold, then, in a w-bit vector is:
$$UMax_w = 2^w - 1$$
So if we had a 4-bit number, the maximum value that number can have is $2^4 - 1 = 16 - 1 = 15$.
- It should be noted that the function $B2U_w$ is a bijection, which is to say that it goes both ways, or has an inverse.
	- What this means is that while $B2U_w$ converts binary to decimal, there exists a $U2B_w$ (Unsigned to Binary) which converts a decimal value into binary.
## Unsigned to Binary $U2B_w$
The simple way of doing this is as follows:
$$
\begin{cases}
N_0 = N \\
r_i = N_i \bmod 2 \\
N_{i+1} = \left\lfloor \frac{N_i}{2} \right\rfloor
\end{cases}
\quad \text{for } i = 0, 1, 2, \ldots
$$

$$
\text{Stop when } N_{i} = 0
$$

$$
\text{Binary digits} = \{r_{i-1}, r_{i-2}, \ldots, r_0\} \quad \text{(read in reverse order)}
$$
Example of this in action with 43:$$
\begin{align}
\frac{43}{2} &= 21,\ \text{remainder = 1} \\
\frac{21}{2} &= 10,\ \text{remainder = 1} \\
\frac{10}{2} &= 5,\ \text{remainder = 0} \\
\frac{5}{2}  &= 2,\ \text{remainder = 1} \\
\frac{2}{2}  &= 1,\ \text{remainder = 0} \\
\frac{1}{2}  &= 0,\ \text{remainder = 1}
\end{align}
$$

When read in reverse, the binary representation of $43_{10}$ is $101011_2$
# Two's Complement Encodings
- Writing just positive (unsigned) integers are not enough, we need to write negative values as well.
	- This is where the two's complement representation comes in.
For vector $\vec{x} = [x_{x-1},x_{w-2}, ..., x_0]$:
$$B2T_w(\vec{x})\doteq -x_{w-1}2^{w-1}+\sum_{i=0}^{w-2}x_i2^i$$

