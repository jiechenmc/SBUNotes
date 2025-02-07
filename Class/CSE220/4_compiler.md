---
layout: post
title: C Compiler
tags: C
---

1. C **preprocessor** replace \#include and \#macro
2. C **compiler** compiles to human readable assembly code (.s)
3. The **assembler** converts that to object file (.o)
4. The **linker** links the object files to create a executable


cc -E | preprocessor step
cc -S | stops at assembly
cc -c | creates object files
cc -o | creates the executable
