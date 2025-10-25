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
- The simple way of doing this is as follows:
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
- Example of this in action with 43:
$$
\begin{align}
\frac{43}{2} &= 21,\ \text{remainder = 1} \\
\frac{21}{2} &= 10,\ \text{remainder = 1} \\
\frac{10}{2} &= 5,\ \text{remainder = 0} \\
\frac{5}{2}  &= 2,\ \text{remainder = 1} \\
\frac{2}{2}  &= 1,\ \text{remainder = 0} \\
\frac{1}{2}  &= 0,\ \text{remainder = 1}
\end{align}$$

- When read in reverse, the binary representation of $43_{10}$ is $101011_2$
# Two's Complement Encodings
- Writing just positive (unsigned) integers are not enough, we need to write negative values as well.
	- This is where the two's complement representation comes in.
For vector $\vec{x} = [x_{x-1},x_{w-2}, ..., x_0]$:
$$B2T_w(\vec{x})\doteq -x_{w-1}2^{w-1}+\sum_{i=0}^{w-2}x_i2^i$$
A list of examples of this in action (it's converting binary to decimal):
$$B2T_w([0001])=-0*2^3+0*2^2+0*2^1+1*2^0=-0+0+0+1 = 1$$
$$B2T_w([0101])=-0*2^3+1*2^2+0*2^2+1*2^0=-0+4+0+1=5$$
$$B2T_w([1011])=-1*2^3+0*2^2+1*2^2+1*2^0=-8+0+2+1=-5$$
$$B2T_w([1111])=-1*2^3+1*2^2+1*2^2+1*2^0=-8+4+2+1=-1$$

Just like the unsigned encodings twos complement also has an inverse (converts decimal to twos complement encoded binary) $T2B_w$
### Conversion from Twos complement to unsigned is as follows:
For $x$ such that $TMin_w \leq x \leq TMax_w$:
$$
T2w(x) = 
\begin{cases}
x + 2w, & \text{if } x < 0 \\
x, & \text{if } x \geq 0
\end{cases}
$$
### Conversion from unsigned to twos complement is as follows:
For $u$ such that $0 \leq u \leq UMax_w$:
$$
U2W(x) = 
\begin{cases}
u, & \text{if } u \leq TMax_w \\
u-2^w, & \text{if } u > TMax_w
\end{cases}
$$
# Alternative Methods of Encoding Signed Numbers
- Should be noted that two's complement is considered standard and that these other 2 encodings are seldom used.
## One's Complement
It's the same as twos complement ($B2T_w$) but the most significant bit has weight $-(2^{w-1}-1)$ rather than $-2^{w-1}$:
$$B2O_w(\vec{x})\doteq -x_{w-1}(2^{w-1}-1)+\sum_{i=0}^{w-2}x_i2^i$$
An example of one's complement in action (once again, it is converting binary to a signed decimal number):
- There are two ways of pulling this off.
### Simple Way:
- You can convert the binary to one's complement encoded binary by flipping the 1s and 0s.
	- E.g., $00001011_2$ ($11_{10}$) in unsigned binary is $11110100_2$ in one's complement binary and represents $-11_{10}$.
		- The math for this can be done like so:
			- You need to flip it again so $11110100_2$ turns into $00001011_2$ then because the sign bit of the one's complement (pre-flip) was negative, you multiply it by -1, so you get: $-1*11=-11$.
		- Should also be noted that one's complement signed numbers will not have the same range as unsigned numbers (you will need more bits at times to represent the same number as a negative number as unsigned has twice the range of signed).
- A quirk of one's complement is that it has 2 representations for zero: $0000_2$ which represents positive zero, and $1111_2$ which represents negative zero.
## Sign Magnitude
- In sign magnitude, the most significant bit is a sign bit that determines whether the remaining bits should be given positive or negative weight:
$$B2S_w(\vec{x})\doteq (-1)^{x_{w-1}}*(\sum_{i=0}^{w-2}x_i2^i)$$
# Expanding the Bit Representation of a Number
- This happens when you cast from a smaller data type (like `short`) to a larger data type (like `int`).
	- See also: [[Integer Representations#Integral Data Types|Integral data types in C]].
## Zero Extension
- To convert an unsigned number into a larger data type we can simply adding leading zeroes to the representation, the value remains unchanged.
	- E.g., casting a `short` (2 bytes) $1111 1010_2$ to `int` (4 bytes) would result in $0000 0000 1111 1010_2$. Both of which represent the same number as the leading zeroes do not add anything to the original value.
## Sign Extension
- This is what we'd use for signed data types as adding leading zeroes to a signed data type will switch its value (think: $1010_2$ in twos complement binary represents $-6_{10}$ adding zeroes to this will actually change the sign of the number and make it a positive number).
	- See also: [[#Two's Complement Encodings|Binary representation of signed numbers]].
- As such, instead of filling the leading bits with zeroes, we can fill it with copies of the sign bit, not also how this does not change the value of the number either.
	- E.g., $0101_2 = 5_{10} = 00000101_2$ (filled with 0 as that is the sign bit) and $1101_2 = -3_{10} = 11111101_2$ (filled with 1 as that is the sign bit).
# Truncating Numbers
- This happens when you cast from a larger data type to a smaller data type (think about it: if you have a larger data type, it likely has more data (e.g., a bigger number), so when you cast it to a smaller data type it will lose some data).
- When a number is truncating the higher order bits (most significant bits) are discarded.
- For **unsigned** bits the new number becomes $x\pmod{2^k}$ where $x$ is the original number and $k$ represents the new, smaller, number of bits.
	- E.g., Converting $1010 0111_2$ from 8 bits to 4 bits will result in $0111_2$ as the 4 higher order bits are discarded, using the equation we can double check this as $1010 0111_2=167_{10}$ and ${167\pmod{2^4}=167\pmod{16}=7}$ and $0111_2=7_{10}$.
- For **signed** bits the higher order bits are removed but the new resulting binary is re-interpreted as a two's complement number where the new most significant bit becomes the sign bit.
	- E.g., Converting $167_{10}$ from 9 bits to 4 will result in the first 5 bits of $010100111_2$ (note that this is different from the representation of $167_{10}$ from the previous example as this is the twos complement representation of $167_{10}$ which is a 9 bit number) being removed, resulting in $0111_2$ here the MSB is a positive number so the new number actually becomes ${7_{10}}$.
	- This is tricky and truncating often results in data loss or bad numbers.