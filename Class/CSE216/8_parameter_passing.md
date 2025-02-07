---
layout: post
title: Parameter Passing
tags: java
---

> [!note] > Everything in Java is pass by value 
> Reference types will have their pointers copied
> Primitive types will have their values copied
> **bitwise operators** are evaluated eagerly in most languages

### Pass by Value (Eager)
- Arguments are fully evaluated before the function is invoked
	- Resulting value is copied into some location and will exist throughout the function execution
	- (Java) "location" is a chunk of memory in the runtime stack
- Arguments are protected from modification
```java
static void f(int x) { x = 3; }
static int x = 0;
public static void main(String[] args) {
	f(x);
	System.out.printf("%d\n", x); // prints 0
}
```

### Pass by Name (Lazy)
- The argument is evaluated as late as possible
- Great for creating non-strict programs
	- Control structure of the type
	- Infinite data structures like streams
- The parameter is a literal substitution of the argument
```ocaml
let add x y = x + y;;
add (a * b) (c * d);;
(* Evaluated as (a * b) + (c * d) *)
```

### Ref Type in Ocaml
- Basically pointers
```ocaml
let x = int ref;;  (* similiar to int* in C *)
!x;; (* dereferencing x *)
```

### Thunks
	A thunk is a subroutine used to inject an additional calculation into another subroutine. They are primarily used to delay a calculation until its result is needed, or to insert operations at the beginning or end of the other subroutine.

	Delaying calculation is done by taking an function, and replacing each argument with a thunk that evaluates that argument.
