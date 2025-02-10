---
layout: post
title: Go Language Features
tags:
  - go
  - language
---
# Control Flow

You can execute a statement in the if and switch blocks.

```go
if expr; compare {

}

// OR

switch expr; (variable) {

}
```

Variables declared are scoped to the if statement but it is shared with any else statment.

The `break` in switch is implicit, and the cases can take any value.

The `defer` statement's function call arguments are evaluated immediately, but the function call does not happen until the surrounding function returns.

`defer` calls are pushed onto a stack, LIFO.

When you `panic`, all the defer calls are executed.

# Pointers

Go has no pointer arithmetic
Go has implicit deference for accessing fields
- This is similar to `p->X` in `C`.

```go
type Vertex struct {
	X int
	Y int
}

func main() {
	v := Vertex{1, 2}
	p := &v
	p.X = 1e9
	fmt.Println(v)
}
```

# Struct Literals

```go
Vertex{}
```

This will initialize every field to 0

# Arrays

```go
[n]T
```

Declares an array of type, T of size n.

# Slices

You can create slices from arrays.

```go
a[low:high)
```

The slice is a shallow copy of the original, so they share reference. Each slice has a length and capacity. The `capacity` is how many elements in the underlying array and the `length` is the number of elements the slice contains.

`Capcity` can change when you drop elements from the slice.
`Length` can change when you slice in the middle as well as add/drop elements.

# Dynamic array

You can use `make()` to create a slice. When you append, a bigger array will be allocated if there is not enough space.

- Similar to `calloc()` in `C`.

# Range

- Similar to Python.

# Closure

- Similar to JavaScript.

# Methods

```go
// Value Receiver
func(receiver T) name rtype {
	// In here you have access to the receiver
	fmt.Println(receiver.Field)
}

// Or Pointer Receiver

func(receiver *T) name rtype {
	// In here you can access and **modify** the receiver
	// Pointer receiver also avoids copying the value on each method call
	receiver.Field = somethingelse
}
```

Depending on the receiver, Go will automatically interpret the value correctly (either as value or pointer).

# Interface

```go
func main() {
	var i I

	i = &T{"Hello"} // (&{Hello}, *main.T)
	describe(i)
	i.M()

	i = F(math.Pi)
	describe(i) // (3.141592653589793, main.F)
	i.M()
}
```

Defines a set of method signatures. No `Implements` keyword, it is implicit. An interface is a tuple `(value, type)` that holds a concrete type.

If there is no concrete type, then it will segfault.