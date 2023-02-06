

>[!info] The range of digits for a base, b, is [0, b - 1]

## _Ranges_

| Representation   | Range                       |
| ---------------- | --------------------------- |
| Unsigned Integer | [0, 2$^n$ - 1]              |
| Signed Integer   | [-2$^n-1$ + 1, 2$^n-1$ - 1] |
| One's Complement | [-2$^n-1$ + 1, 2$^n-1$ - 1] |
| Two's Complement | [-2$^n-1$, 2$^n-1$ - 1]     |

>**End around carry** only exists in one's complement
>You **drop** the extra bit in two's complement

## _Overflow_

- Two's Complement
	- When adding the same signs
- Unsigned
	- When you have an extra bit in the result
	- This can cause inaccurate answers

## _Encoding_

- Two Complement Encoding
	- Multiplication by 2
		- Introduce 0 at right (\<\< 1)
	- Division by 2
		- Drop rightmost bit (\>\> 1)
		- Then replicate the sign bit
	- Bitwise multiplication and division can be can with any powers of 2
		- Multiplication by 8 will be num \<\< 3

- Excess-k Encoding
	- Expressed as unsigned value


## _IEEE 754_

#### Normalization
1011 \* $2^0$
1.011 \* $2^3$

e = 3

Range of excess 127 is [-127, 128]

####  32 bit
| 1 bit sign | 8 bit exponent | 23 bit mantissa |excess-127     | 
| ---------- | -------------- | --------------- | --- |

#### 64 bit
| 1 bit sign | 11 bit exponent | 52 bit mantissa | excess-1023 | 
| ---------- | --------------- | --------------- | ----------- |
