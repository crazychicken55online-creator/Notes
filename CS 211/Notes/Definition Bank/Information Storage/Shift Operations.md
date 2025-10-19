# Left Shift
`x << k` is a left shift (note how it points towards the left).
- This shifts `x` `k` bits to the left, dropping off the `k` most significant bits and filling the right end with 0s.
	- Another way to think about it is that it removes `k` bits from the left and pads `k` zeroes to the right.
	- E.g., `x = 1010111`, `k = 3`, `x << k`, then `x = 0111000`
# Right Shift
`x >> k` is a right shift (note how it points towards the right), it has 2 variations.
- Should be noted that almost all compilers use arithmetic right shifts for signed data. 
- Should also be noted that in Java, unlike C, arithmetic right shifts are defined as `x >> k` and logical right shifts are defined as `x >>> k` 
## Logical
- This shifts `x` `k` bits to the right, dropping off the `k` least significant bits and filling the left end with 0s.
	- Another way to think about it is that it removes `k` bits from the right and pads `k` zeroes to the left.
	- E.g., `x = 1010111`, `k = 3`, `x >> k`, then `x = 0001010`
# Arithmetic
- This shifts `x` `k` bits to the right, dropping off the `k` least significant bits and filling the left end with the most significant bit.
	- Another way to think about it is that it removes `k` bits from the right and pads `k` repetitions of the most significant bit to the left.
	- E.g., `x = 1010111`, `k = 3`, `x >> k`, then `x = 1111010`

