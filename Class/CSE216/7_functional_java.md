---
layout: post
title: Functional Programming in Java
tags: java
---

# What is functional programming?

>[!info] No concept of internal state
> Once a variable is assigned it should not be reassigned; we can create new variables and not modify existing variables

>[!info] No side effects ("pure")
> It does not modify state outside the function

# Features

1. Functions are first class values
   - can be passed in as a parameter
   - can be returned
   - and assigned to a variable
2. High order functions
   - functions can take other functions as parameters, and/or return a function
3. Polymorphism 
   - either inherently polymorphic because of dynamic typing or due to type inference
4. Aggregates for structured objects
   - anonymous functions; lambda expressions
5. Garbage Collection
   - Limited Extent
	   - local variables stored in the stack will get thrown away after the function has been used
   - Unlimited Extent
	   - objects that persist as long as there is a reference to them
   - All dynamically allocated data is stored in the heap

# Evaluation

| Normal Order                                     | Applicative-order                            |
| ------------------------------------------------ | -------------------------------------------- |
| The left-most function is always evaluated first | The inner most functions are evaluated first |
| Evaluated when they are actually used            | Evaluated as they are passed in              |

>[!info] Lazy Evaluation
> With lazy evaluation, the evaluation is delayed (until needed) in a way that avoids multiple evaluations of the same expression.
> - All copies of that expression are updated with the value.
> - ==Stream\<T\>== or ==Iterable\<T\>== creates a collection that uses lazy evaluation

>[!info] Strict & Non-strict evaluation
> A function is strict if it is **undefined** (fails to terminate or encounters an error); whenever its argument(s) is/are undefined
> - Eager evaluation is strict
> - Lazy evaluation is non-strict

>[!info] Java and Python uses lazy evaluation for its binary logical operators

>[!info] Java uses eager, applicative-order evaluation for method arguments.

>[!info] Lazy Class Loading
>A class is loaded into memory only when they are first referenced. This can happen in two ways:
> 1. // first call to a static method in a class
> 	`MyClass.aMethod();`
> 2. // first instantiation of an object
> 	`MyObject o = new MyObject();`
>

>[!info] Laziness of Streams
>1. Intermediate: map() and filter()
> 	  - Calls to them return immediately and the lambda expressions provided to them are not evaluated right away.
>2. Terminal: reduce()
> 	  - The behavior of intermediate operations is ‘cached’, and used only when the terminal operation is invoked.
> - Every operation before the last one is **intermediate**; terminal is the last operation
> - Streams do just enough work to satisfy the **terminal** operation
