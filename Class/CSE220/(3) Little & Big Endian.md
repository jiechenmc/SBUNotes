#concept #hardware

LSB = Least Significiant Byte
MSB = Most Significiant Byte

Endianness governs how bytes are placed in memory.

### Little Endian (Reverse Order)

>[!info] LSB is stored at the lowest address
>Read **Right to Left** or **Up Down**

### Big Endian (Normal Order)

>[!info] MSB is stored at the lowest address
>Read **Left to Right ** or **Down Up**

You want to read in a way where you get the **MSB first**. Hence why, Little Endian is right to left and Big Endian is left to right.