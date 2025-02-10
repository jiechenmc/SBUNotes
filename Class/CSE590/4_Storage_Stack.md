---
layout: post
title: Storage Stack
tags:
  - linux
  - kernel
---
1. The lowest: hardware
	- Though itself may have many layers: firmware, caching, physical media
2. Middle: OS
3. Upper: user/applications, networks, cloud, etc...
	- low level libraries (libc)
	- middlware libraries (libssl)
	- applications (e.g, web servers)

# OS Expanded (Lowest -> Highest)

1. Device Drivers
	- standardize access to devices
	- understand specifics such as read/write, spin up/down
	- exists so that the upper layers use a unified API
2. I/O Schedulers
	- Decides what to send the disk and in what order
	- Requests to read/write LBAs may come from different apps/sources
	- Requests may interleave in any order

Assume a HDD has 100 tracks, each track with 100 LBA.
Requests come in for 1, 300, 3, 400, 730, 402

The **naive scheduler** will read this in the order received. This results in high latency with all the head movement.

The **better scheduler** will sort the request by LBA # to minimize head seeks. Once the head is at the innermost track, then we can reverse sort the next set of requests, and read LBAs in descending order. 

More formally, this is the elevator algorithm.

>[!info] Elevator Algorithm
>1. Monitor the position of the HDD head using control codes
>2. Sort the requests in ascending/descending order
>3. Send the requests to the HDD
>4. Repeat steps 1-3 alternating in sorting order
>   
>This sweeps the HDD back and forth

Given N requests, wait up to time T.

If N = 1: essentially sending requests in FCFS order, can result in random seeks. This is sometimes called the "noop". 

>[!tip]
>A small N will result in more randomness.

If N is large, then you ware waiting too long to submit requests, resulting in artificial delays that can be worse than head seeks. 

The right value for N depends on many factors:

- The load on the system
- The speed
- The kinds of applications
- Users preferences

This is why many I/O schedulers have configurable parameters.

T: How long to wait before submitting I/O

There are many I/O schedulers in existence and optimized for different things:

- Specific complex workloads (eg., databases)
- Specific devices or device types
- Parallelism in some systems: multi-queue I/O scheduler
- Priority Queues
- Optimizing for access patterns: temporal, frequency based
- Follow similar algorithms for process/thread schedulers

If the device is busy, the I/O scheduler can sense it using control commands (are you free or busy?)

>[!important]
> If the disk is busy a lot of the time, then the queue in the I/O scheduler starts growing and eventually upper layers will slow down as well, until the application is slowed and even suspended (throttled).
