# Unsigned Addition
- Unsigned binary addition works the same as regular binary addition, with the change that if the resulting binary post addition has more bits than the maximum allowed, then the last max allowed bits are kept.
	- Note that with binary addition 1+0 = 1, 0+0=0, and 1+0=10
	- E.g., $11111010_2 + 00001010_2 = 100000100_2$ however only the first 8 bits are kept, $00000100_2$. 
# Two's Complement Addition
- The core addition is done the same way as regular binary addition, however the interpretation of overflow is different.