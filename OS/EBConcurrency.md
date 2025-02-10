---
layout: post
title: Event Based Concurrency
tags: linux concurrency
---
# Event Based Concurrency

`select()` and `poll()` system calls can be used to check if a fd is ready for reads or writes.

An event based concurrency approach like event loops avoids locks but can still be blocked by page faults.

State management is done with continuation where a datastructure like a hashtable is updated when an I/O event completes.
