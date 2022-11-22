#concept #java 

> [!note] > Everything in Java is pass by value 
> Reference types will have their pointers copied
> Primitive types will have their values copied

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