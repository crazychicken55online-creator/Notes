# Fractional Binary Numbers
- Same as fractional decimal numbers, they're binary representations of fractional numbers and such they include a "binary point". Think of it has how the 0.25 is the decimal representation of the fractional number $\frac{1}{4}$ and has a "decimal point" between 0 and 25.
- Just like how in decimal, digits to the left have weights 1, 10, 100, etc. and digits to the right have weights $\frac{1}{10}, \frac{1}{100}, \frac{1}{1000}$, etc. In binary, the bits to the left have weights 1, 2, 4, etc. and the bits to the right have weights $\frac{1}{2}, \frac{1}{4}, \frac{1}{8},$ etc.
- Note that just like how $\frac{1}{3}$ cannot be represented perfectly in decimal, numbers like $\frac{1}{5}$ cannot be represented perfectly in binary.
# IEEE Floating-Point Representation
- See also: [Floating Point Visually Explained](https://fabiensanglard.net/floating_point_visually_explained/)
- IEEE, or IEEE 754, is the technical standard for representing floating point (real) numbers in binary. You can think of it as the binary version of scientific notation.
$$V=(-1)^S\times M\times2^{E}$$
- The bits of a float (32-bit) and a double (64-bit) are split into 3 parts:
	- s: The sign bit (1 bit), 0 or 1.
	- exp: The exponent field (k bits), encodes the exponent E.
		- 8 bits for floats, 11 bits for doubles.
	- frac: The fraction field (n bits), encodes the significand (sometimes referred to as mantissa) M.
		- 23 bits for floats, 52 bits for doubles.
- There are 3 types of values based on the exp field:

| Case | exp Field            | frac Field | Type         | Exponent (E) | Significand/Mantissa (M) |
| ---- | -------------------- | ---------- | ------------ | ------------ | ------------------------ |
| 1    | Not all 0s or all 1s | Any        | Normalized   | e-Bias       | 1+f                      |
| 2    | All 0s               | Any        | Denormalized | 1-Bias       | f                        |
| 3a   | All 1s               | All 0s     | Infinity     | N/A          | N/A                      |
| 3b   | All 1s               | Not all 0s | NaN          | N/A          | N/A                      |
- Terms:
	- e: The **unsigned** integer value of the exp field.
	- f: The fractional value of the frac field (e.g., $0.f_1f_2f_3...$)
	- Bias: A constant $2^{k-1}-1$ (127 for float, and 1023 for double).
- Case 1: Normalized:
	- In the "normal" case the binary number is always between 1 and 2 $[1,2)$, this means that the first bit is **always** 1, this allows us to just do 1+f and gain an extra bit of precision in the fractional part of the floating point as we do not need to represent the 1 (it's given) and can use that to gain extra precision.
		- In short, since the 1 is guaranteed to be there (the number will be 1.xx) the computer doesn't store it and instead only stored the part after 1 (the fractional part f) and later adds 1 to it in order to get the full number.
- Case 2: Denormalized:
	- The denormalized case handles numbers that are extremely close to zero and are too small to be represented in the normal way.
	- The implied leading 1 is gone and instead there is a leading 0, so you don't gain that extra bit of precision.
	- The significand (mantissa) becomes 0+f instead of 1+f.
	- The overall value becomes $\pm 0.f\times 2^{\text{Min Exponent}}$
		- Here this means that instead of using the bias and storing the exponent as an unsigned number and then subtracting the bias to get the true exponent, we use the minimum possible exponent for the data type.
			- The minimum exponent is $1-\text{Bias}$ where the bias is $\text{Bias}=2^{k-1}-1$ where k is the number of bits in the exponent field.
				- For floats the minimum exponent is -126.
				- For doubles the minimum exponent is -1022.
- Case 3: Special Cases:
	- This occurs when the exponent field is all 1s.
	- If the fractional field is all zeroes then the value is infinity $\pm\infty$.
		- E.g., $\frac{1.0}{0.0}$
	- If the fractional field is **NOT** all zeroes (could be **ANYTHING** else), the value is `NaN` (Not A Number).
		- E.g., $\sqrt{-1}$
# Example: Encoding a Number
E.g., Represent $x=-0.75$ as a float (32-bit).
- Sign bit, s = 1 as -0.75 is a negative number.
- The integer part is 0 as 0.75 leads with a 0 before the fractional value.
- For the fractional part:
	- $0.75\times 2 = 1.50$, leading 1 so the first bit after the "binary point" is 1.
	- $0.50\times 2 = 1.00$, leading 1 = 1 so the second bit after the "binary point" is 1.
	- We end here as we have 0.00 left.
	- So $0.75_{10}=0.11_{2}$
- Normalizing the binary number:
	- The number needs to be represented in the normalized form: $1.F\times 2^E$.
	- For $0.11_2$ we just need to move the first 1 from the right side to the left: $0.11_2=1.1\times 2^{-1}$
	- From this we get the true exponent: -1 and the fractional bits after the "binary point".
- Calculating the biased exponent (8 bits as it is a float):
	- Biased exponent = $E_{true}+\text{Bias}$
		- $\text{Bias}=2^{8}-1=128-1=127$
	- Biased exponent = $-1+127=126$
	- Convert $126_{10}$ to binary:
		- $126_{10}=64_{10}+32+{10}+16_{10}+8_{10}+4_{10}+2_{10}=01111110_2$
	- Exponent = $126_{10} = 01111110_2$
- Find the fraction (Significand/Mantissa, F):
	- The fraction F is the part of the normalized number that comes after the leading 1.
		- From the previous steps we found that the fraction part is 1. (Comes from $1.1\times 2^{-1})$
		- The fraction field **must** be 23 bits long for floats. As such we pad the **right** with 0s.
			- Note that we are padding the right and not the left because for numbers after the decimal point the value doesn't take if you add 0s to the right but does change if you add it to the left, it is the opposite for numbers on the left side of the decimal point.
			- $F = 1\underbrace{0000000000000000000000}_{22 \text{ zeros}}$
- Putting it all together:
	- Note that you need to put it in this order: sign bit (s), then exponent (E), then fraction (F).

| Part                   | Value | Binary Representation   |
| ---------------------- | ----- | ----------------------- |
| Sign (S) (1 bit)       | 1     | 1                       |
| Exponent (E) (8 bits)  | 126   | 01111110                |
| Fraction (F) (23 bits) | 0.1   | 10000000000000000000000 |
Final binary representation: $1\ 01111110\ 10000000000000000000000_2$
# Rounding
- IEEE 754 defines four rounding modes. The default is Round-to-Nearest (also known as Round-to-Even).
- Round-to-even rounds to the nearest representable number.
	- If a number if **exactly** half way between 2 representable numbers, it rounds to the one that makes the **least significant bit** **even**.
		- This avoids the statistical bias of always rounding 0.5 up.
	- E.g., 1.23 rounds to 1.2, 1.27 rounds to 1.3, 1.25 rounds to 1.2 (2 is even), 1.35 rounds to 1.4 (4 is even).
# Floating Point Operations
- The result of a floating point operation is the exact mathematical value of that operation, it is rounded after the calculation to fit the format.
- Floating point operations are not associative or distributive.
- Floating point multiplication and addition are both commutative.
# Floating Point in C
- C has 2 types of floating points, `float` and `double`.
- Results of type casting floating points with various data types:
	- `int` to `float`: May round, but won't overflow.
	- `int` or `float` to `double`: Value is preserved exactly. 
	- `double` to `float`: May round and may overflow to $\pm\infty$.
	- `float` or `double` to `int`: **Rounds toward zero.** May overflow.