#concept #hardware

LSB = Least Significiant Byte
MSB = Most Significiant Byte
TD = Top Down
DU = Down Up

Endianness governs how bytes are placed in memory.

### Little Endian (Reverse Order; RTL, TD)

>[!info] LSB is stored at the lowest address
>Read **Right to Left** or **Up Down**
>**LSB** ... **MSB**

### Big Endian (Normal Order; LTR, DU)

>[!info] MSB is stored at the lowest address
>Read **Left to Right ** or **Down Up**
>**MSB** ... **LSB**

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


