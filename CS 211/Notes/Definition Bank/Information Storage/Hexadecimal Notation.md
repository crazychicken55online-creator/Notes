- Hexadecimal notation uses 0 through 9, along with the characters A through F to represent 16 possible values. 
	- Note that the characters A through F could be in uppercase **or** lowercase.
- Written in hexadecimal, a value of a single byte can range from $00_{16}$ to $\text{FF}_{16}$.
- In C hexadecimal numbers start with 0x or 0X.
> [!example] Hexadecimal Notation
> ![[Hexadecimal Notation Table.png]]
# Converting Hexadecimal to Binary
- Converting hexadecimal to binary requires you to expand each hexadecimal digit into its equivalent, 4 digit, binary representation.
E.g., Convert $\text{0x173A4C}$ to binary:

| Hexadecimal | 1    | 7    | 3    | A    | 4    | C    |
| ----------- | ---- | ---- | ---- | ---- | ---- | ---- |
| Binary      | 0001 | 0111 | 0011 | 1010 | 0100 | 1100 |
Putting it all together: $\text{0x173A4C}$ in binary is $000101110011101001001100_2$
- Note that you must always use 4 digits for the binary form, e.g., $\text{0x1}$ will be $0001_2$ in binary, not just $1_2$.
# Converting Binary to Hexadecimal
- Converting binary to hexadecimal requires you to split the binary representation into 4 digit chunks, and then convert each chunk to its hexadecimal equivalent.
E.g., Convert $1111001010110110110011_2$ to hexadecimal:
You will notice that this is not evenly divisible by 4, which is to say that you cannot split the above binary number into 4 digit hexadecimal chunks, there are 2 digits too many.
In this situation, we must pad the beginning of the number with enough 0s such that you are able to make even 4 digit chunks.
- As such for this example the binary number we will convert will end up being $001111001010110110110011_2$
	- Notice that adding 0s to the beginning of a binary number does not change its overall value, $0001_{2}$ and $1_2$ both represent the number $1_{10}$.

| Binary      | 0011 | 1100 | 1010 | 1101 | 1011 | 0011 |
| ----------- | ---- | ---- | ---- | ---- | ---- | ---- |
| Hexadecimal | 3    | C    | A    | D    | B    | 3    |
Putting it all together: $1111001010110110110011_2$ in hexadecimal is $\text{0x3CADB3}$.