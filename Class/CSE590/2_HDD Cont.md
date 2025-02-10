---
layout: post
title: HDD Cont
tags:
  - hardware
---
# How much data to access?
- latencies are high
- get too little data and time spent on latency will be wasted
- get too much data and there is no room to hold

# Units of Measurement

**CPU**
- Word Length
	- Used to be 32b; 64b on modern machines
**MEM**
 - Page Size
	 - Usually 4kb
	 - Determined by CPU + Memory Architecture 
	 - AMD and Intel introduced memory buses to speed up data transfer between RAM and CPU
**Network**
- MTU
	- 1500b
**Storage**
- Sector size of 512B (c. 1960s)
- Around c. 2010 it grew to 4KB
	- The increased size matches CPU page size and better for caching
- OS offers backwards compatibility between 512B and 4KB sector sizes

>[!warning]
> Writing 512b to a 4Kb sector is **bad**
> 
> -> OS sends write
> -> OS read 4Kb sector
> -> Store in disk cache
> -> Write back entire 4Kb
> 
> Read-Modify-Write (RMW) patter; bad performance

# How to address sectors?

In the old days, OS drivers provided "CHS" values
- C: Cylinder, concentric circles around the platter
- H: Head, which head to access
- S: Sector, region on the cylinder for specific head

CHS was proven to be too complex.

Now, disk vendors assign a number (ID) to each sector in some order
- It can be in any order the vendor desired top/bottom, outer/inner, from one head to another, etc...
- These ids are called Logical Block Address (LBA) number

OS software just has to ask the disk to read/write to LBA # 
- Disk will internally figure out where that LBA is
- Simplifies addressing

Often, LBAs were assigned from the outer cylinder, so lower LBA performed better.
	- **Rotational latency is better than head seek**


# Remap Table

Disks maintain metadata in **remap table**.
- With wear and tear, some LBA will die
- Not exposed to the OS
- When reading sequential data with a remap, you have to detour
	- **Hurts Performance**

When the remap table fills up too much, no more bad blocks can be remapped, and performance devolves into random access. If the table is full, then the disk is dead.

Disks can die in the first 3 months ("infant mortality), due to manufacturing defects, transportation, high loads, etc...

Vendors will determine if disks are consumer vs. enterprise grade based on hardware quality.