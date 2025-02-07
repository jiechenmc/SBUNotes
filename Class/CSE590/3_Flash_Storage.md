---
layout: post
title: Flash Storage
tags:
  - hardware
---
# Control Codes

1. S.M.A.R.T
2. Spin Up/Down
3. Write Barrier

# S.M.A.R.T

A set of commands to get status info on a disk. 
- make, model, size, manufacturing date
- number of read and writes that took place
- remap table size and fullness

# Write Barriers

Write barriers are used by applications and the OS to ensure that data up to point T is flushed and persistent to disk. Users and applications can use `fsync/sync/fflush/` syscalls to tell the OS to flush its data all the way down to disks and they flush theirs.

Normally, writes to disk keep dirty data in HDD's cache. Firmware will pick up those dirty writes eventually and flush them to media.

If HDD detects power failure, it has to flush dirty buffers quickly before the platters lose enough speed and head can not be moved.

As power is draining, the content of DRAM tends to fluctuate. DRAM content could get corrupted as you flush. Worst case is to flush corrupt data persistently.

## Popular Uses

- Databases to store their transaction logs
- Filesystems to write their journals
- Applications that need to write important metadata

>[!info]
>If you overuse flush, it will slow down your system!

# Failure Modes in Disks

1. Sectors going bad, can be remapped
2. Electronic dies, or motor fail, actuator that moves head
3. Bits are lost over time, "bitrot", use internal ECC to recover or external integrity (eg., RAID)
4. Disks do not flush data; bad firmware; manufacturing issue
5. Firmware bugs can result in "lost write" or "misdirected write"