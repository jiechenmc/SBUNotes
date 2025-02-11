---
layout: post
title: Filesystem Demo
tags:
  - linux
  - filesystem
---
# Man Page Sections

1. Basic Unix commands
2. Syscalls
3. Library Calls
4. System Administrator privileged commands (sudo)

# Unix Timestamps

1. access; when file was last read `atime`
2. modify; when file content last changed `mtime`
3. change; when inode last changed `ctime`
4. MacOS added "birth time" or true file creation time

# `stat` Example

The file was created by running:

`echo hello world > foo`

```bash
  File: foo

  Size: 12        Blocks: 8          IO Block: 4096   regular file

Device: 259,2 Inode: 19398749    Links: 1

Access: (0644/-rw-r--r--)  Uid: ( 1000/  ubuntu)   Gid: ( 1000/  ubuntu)

Access: 2025-02-11 14:51:50.228031173 -0500

Modify: 2025-02-11 14:51:59.248325097 -0500

Change: 2025-02-11 14:51:59.248325097 -0500

 Birth: 2025-02-11 14:51:50.228031173 -0500
```

The `stat` command shows a file size size of 12 but 8 blocks were allocated when the filesystem block size is 4096. Why? This because storage devices only allocate in sector/block chunks (512B in this case). You can infer the underlying sector size is 512B by doing 4096 / 8.

# Block allocation flow

- storage devices only allocate in sector sizes (512B in this case)
- filesystem ask disk for at least 1 block (8 blocks in this case)
- filesystem then fill that block with file contents
- filesystem records how many bytes were used out of the allocated blocks

The filesystem presents the 8 blocks to the applications as a single 4096 block.

# Permissions
- only owner can change permission
- only root can chown

The OS decides filesystem block size at format time.
- Smaller block size is better for small file workloads
- Bigger block size is better for larger files (images, videos, etc)
	- This eases the overhead of management.