---
layout: post
title: Endianess
tags: architecture
---

LSB = Least Significant Byte
MSB = Most Significant Byte
TD = Top Down
DU = Down Up

> [!important] Endianness governs how bytes are placed in memory.

### Little Endian (Reverse Order; RTL, TD)

> [!info] LSB is stored at the lowest address
> Read **Right to Left** or **Up Down** >**LSB** ... **MSB**
> LSB will be stored before the MSB
> The addresses are numbered like:
> 5 4 3 2 1 0

> Good for numbers

### Big Endian (Normal Order; LTR, DU)

> [!info] MSB is stored at the lowest address
> Read **Left to Right ** or **Down Up** >**MSB** ... **LSB**
> MSB will be stored before the LSB
> The addresses are numbered like:
> 0 1 2 3 4 5

> Good for strings

You want to read in a way where you get the **MSB first**. Hence why, Little Endian is right to left and Big Endian is left to right.

### Example

You write the integer value 260 (a 4-byte quantity) at address 100.

| Value    | 00000000 | 00000000 | 00000001 | 00000100 |
| -------- | -------- | -------- | -------- | -------- |
| Location | 100      | 101      | 102      | 103      |

The MSB is at address `100` with the value `0`
The LSB is at address `103` with the value `4`

In little endian:
**4, 1, 0, 0**
LSB ... MSB

In big endian:
**0, 0, 1, 4**
MSB ... LSB

<h2> Alignment </h2>
1-byte can be stored anywhere
2-byte can be stored to even-numbered addresses
4-byte can be stored to addresses of multiple of 4
and so forth...

<h2> Little to Big Endian Conversion </h2>
Take the number **258** for example:
In little endian it's stored as 0x2 0x1

1. Convert to bits: (little endian)
   00000010 00000001
2. Flip the bytes (now in big endian)
   00000001 00000010
3. Put them together
   0000000100000010
4. Now calculate
