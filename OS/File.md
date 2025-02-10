---
layout: post
title: File
tags: linux filesystem
---
# Files

A `file` is an array of bytes associated with an inode.

## inodes

Inodes contain information on file type, owner, permissions, timestamps, # of hardlinks, # of blocks, and pointer to data blocks.

## file descriptors (fd)

A `fd` is an index in the open file table that points to an entry in the inode table

To the program, a `fd` the means in which you interact with an open file.

## Hard Links vs Soft Links

Hard links creates a file pointing the same inode of the linked file while soft links only points to the file name.
