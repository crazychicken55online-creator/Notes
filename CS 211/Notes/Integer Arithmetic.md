# Unsigned Addition
- Unsigned binary addition works the same as regular binary addition, with the change that if the resulting binary post addition has more bits than the maximum allowed, then the last max allowed bits are kept.
	- Note that with binary addition 1+0 = 1, 0+0=0, and 1+0=10
	- E.g., $11111010_2 + 00001010_2 = 100000100_2$ however only the first 8 bits are kept, $00000100_2$. 
# Two's Complement Addition
- The core addition is done the same way as regular binary addition, however the interpretation of overflow is different.
- E.g., $11111010_2 + 00001010_2 = 100000100_2$ however only the first 8 bits are kept, $00000100_2$. Notice how $100000100_2$ (the true addition result) is a negative value however the truncated value is a positive value (due to the 0 sign bit).
# Two's Complement Negation
- Negation is the idea of finding $-x$ from $x$
	- See also: [[Operations in Boolean Algebra]]
- The inverse of $x$ is $2^w-x$ where $w$ is the number of bits in $x$
- A bit-level trick that could be used instead is $\sim x+1$
- E.g., If $x=00000010_2=2_{10}$ then $\sim x = 11111101_2$ and $\sim x + 1 = 11111110_2=-2_{10}$
# Unsigned and Twos Complement Multiplication
- The same bit-level multiplication is done for both the unsigned and the twos complement (signed) numbers.
> [!info] Binary Multiplication Reminder
![[Binary Multiplication Visualization.png|500]]
- After performing the multiplication, there is a chance that the resulting binary number is of size $2w$, if so, the computer discards the $w$ higher order bits, leaving the last $w$ bits as the result of binary multiplication.
- The mathematical representation of this is $(x*y)(\mod 2^w)$
# Multiplying by Constants
- Since $x*K$, where x is a number and K is some constant, can be quite slow, compilers use bit shifts and addition.
- Important concept: $x*2^k$ is always `x << k`.
	- Using this idea we need to break the constant K into a sum or difference of powers of 2.
	- E.g., $x*14$:
		- There are two ways of doing this:
		- $14 = 8+4+2$ Code: `(x << 3) + (x << 2) + (x << 1)`
		- $14=16-2$ Code: `(x << 4) - (x << 1)`. Note that this is often faster.
# Dividing by Powers of 2
- Similarly to multiplying, `x >> k` computes $\frac{x}{2^k}$
	- For unsigned numbers we must use the logical right shift (pads with 0s), for signed numbers we must use the arithmetic right shift (pads with sign bit).
		- See also: [[Shift Operations]].
	- E.g., If we want to find $-7/4$ where $x=-7_{10}=11111001_2$ then you'd **NOT** do `x>>2` as $2^2=4$ as that would give you $11111110_2=-2_{10}$ which is wrong. When $x<0$ we must first add the bias $2^k-1$ resulting in $x=-7+(2^2-1)=-7+3=-4$ then if we do `x>>2` then we'd get $11111111_2=-1_{10}$ which is correct.
		- Note that C division rounds down.
	- E.g. 2, If we want to find $7/4$ then we'd set $x=7_{10}=0111_2$ and we'd do `x>>2` getting $0001_2=1_{10}$ which is correct.
	- The C expression depicting this is: `(x<0 ? x+(1<<k)-1 : x) >> k`