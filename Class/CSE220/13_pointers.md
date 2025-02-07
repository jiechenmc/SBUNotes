---
layout: post
title: Pointers
tags: C
---

```C
int n; /* an int variable */ 
int *p; /* a pointer to an int */ 
p = &n; /* p now points to n */ 
/* deferencing a pointer allows you to access and manipulate the data stored at that pointer you can do so by *pointer */ 
*p = 2 
/* p is derefenced, and now n = 2 */
```

Arrays are double pointers

`a` points to the memory address at the start of the array

&a != &a[0]
