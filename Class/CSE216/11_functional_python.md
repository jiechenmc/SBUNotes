---
layout: post
title: Functional Programming
tags: python
---
# Coroutine
>[!info] The terms function or method are synonymous to a subroutine.

>[!info] A coroutine is a generalization of a subroutine. It is a programming unit that can be entered, exited, and resumed from an intermediate state. (Python generators are coroutines)

Concurrency allows for tasks to be performed out of order, even if multiple tasks are not
necessarily being performed at the same time.

# Lambda

a predicate is a function that returns the truth value of some specific condition.

```python
# how we can use lambda to create predicates
lambda x: x <= 10
```
# Partial Application

Suppose we have a function f(x,y,z) and we want to repeatedly use it with x = 1. In that
case, we may want to create a function g(y,z) = f(1,y,z).

```python
def raise2pow(a, b):
	return a ** b

if __name__ == "__main__":
	nth_power_of_2 = partial(raise2pow, 2)
	# 2 is partially applied as the first argument of raise2pow
	# the result is a function g(x) = f(2, x)
	# 2 ** 3 = 8
	print("2 ** {} = {}".format(3, nth_power_of_2(3)))
	square = partial(raise2pow, b=2)
	# 3 ** 2 = 9
	print("{} ** 2 = {}".format(3, square(3)))
```
