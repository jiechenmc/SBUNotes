---
layout: post
title: Processes and Threads
tags: linux virtualization
---
# Process

## fork() vs exec()

The `fork()` syscall creates a new process while `exec()` replaces the running program with a new one. Using `exec()` will deallocate the old address space and load a new program into memory.

You can combine the 2 system calls to create powerful features like the redirection in the shell.

For example, in `cat file > out.txt`, you `fork()`, first `open()` `out.txt` and set the stdout to the fd that was returned, and lastly `exec()` `cat` on `file`.

## signals

Signls are external events you can send to a process. You can use `sigprocmask()` to block a process from receiving certain signals. In the case where a signal is blocked, it will be queued and recieved by the process once unblocked.

# Threads

A multi-threaded program has multiple program counters (PCs). Threads share the address space with the process that created them and has its own stack.

Threads are useful in speeding up computation, avoid blocking I/O, and ideal for shared memory programs.

## address space

The address space of a process contains the code, stack, and heap.

## paging

Paging is chopping up the address space into fixed-size pieces.
