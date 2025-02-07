---
layout: post
title: MIPS
tags: architecture
---

The runtime stacks grow downwards from highest memory address to lower

You use a negative offset to allocate memory for a stack since it grows downwards
To allocate space for 3 registers:
```mips
addi $sp, $sp, -12
```


The heap grows upwards


<h3> $la and $lw </h3>

$la is like the address of operator

$lw is like dereferencing a pointer 

<h3> Registers </h3>

A1, A2, A3 are ids for registers


SW reads from register then stores into memory
LW reads from memory with RD then stored into a register


IN SW rt is stored at A2, that will be where it's stored in the memory


RTYPE instruction has all 0 opcode

RT is the destination for I-type instructions

RD is the destination for R-type instructions
