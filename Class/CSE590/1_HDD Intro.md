---
layout: post
title: HDD Intro
tags:
  - hardware
---
- CPU speeds are in the nanoseconds
- CPU internal speed is 10-100x RAM
- Typical internal memory is from 256 MB to several GB

- DRAM speeds are in microseconds


tldr; Disk are a lot bigger, but they are much slower.

```mermaid
flowchart LR 

CPU -->|1000x faster| DRAM 
DRAM -->|1000x faster| Hard_Disk[Hard Disk] 
CPU -->|1000000x faster| Hard_Disk[Hard Disk] 
```
