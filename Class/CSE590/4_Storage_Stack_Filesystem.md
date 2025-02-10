---
layout: post
title: 4_Storage_Stack_Filesystem
tags:
  - linux
  - filesystem
---
The filesystem provides the abstraction of N x LBAs, whose size is fixed 512B or 4KB to the upper layers.

# What info a file system store?

(a) Files:
- inode; metadata
- content
- the same (sometimes called namespace and sometimes considered metadata)

# File Metadata

- name
- dates; created, modified. access
- size
- type
	- regular file
	- directory
	- symbolic links
	- sockets
	- pipes
	- devices (block and char)
- permissions
- owners, groups
- links or pointers to the data blocks

# Why different types?

- all objects have metadata + inode and possible data
- different types enforce different semantics inside the OS

>[!info] Examples
> Regular Files: open, write, read, close, etc
> 
> Directories: mkdir, rmdir, create, unlink, mknod, unlink, listing, rename
> - Don't allow regular file read/write + seeks (easy to mess up dirent)
>   
> Symlinks: create, delete, follow, read

(b) Directories:
- A table of records <name, inode#>
- When we lookup, we scan the table for a name and return inode #, if not found we return error `ENOENT`.

The inode# alone does not tell what type of file the underlying object is. Historically, some filesystems add/move info to the directory entry, `dirent`. Ex. the type of file of the inode.

You can copy more info but it will be harder to keep them in sync between the `dirent` and the `inode`. 

In a single system, superusers can access the HDD raw data directly and read/write to blocks.

In a networked system, other users from different locations/nodes, or the server could have changed the data.

To delete an entry, zero out the name and mark the inode as free. 
To rename: just change string name; no change to inode. 
To create/mkdir/mknod: allocate a new string + inode

(c) Symlinks:
- Inode and Name
- The "content" is usually capped at 4KB
- The "content" can be interpreted as another path name
- Provides a level of indirection from one named object to another
- A symlink can point to another symlink
- Part of the `namei` lookup process

(d) Pipes:
- A named entity in a directory with Inode
- The read/write is redirected to a process
- Pipes are useful for control command to services
- Ex. Apache may create a pipe for the CLI to send commands to the web server.
