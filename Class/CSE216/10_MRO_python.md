---
layout: post
title: MRO
tags: python
---

>[!info] Python is pass by value!


# Method Resolution Order

```python
class A:
	def m(self):
	print("m of A called")

class B(A):
	def m(self):
	print("m of B called")

class C(A):
	def m(self):
	print("m of C called")

class D(B, C): 
	pass

#    A
#  /   \
# B     C
#  \   /
#    D

# The MRO is D, B, C, A
x = D()
x.m() # prints: m of B called
```
