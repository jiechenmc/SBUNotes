Struct are distinct

part2 = part1 won't create an alias like Java would with reference types

Passing a structure to a function and returning a structure from a function both
require making a copy of all members in the structure.

You can add a "tag" to an union by wrapping it in a struct

```c
typedef struct {
	int kind; /* tag field */
	union {
		int i;
		double d;
	} u;
} Number;
```

<h3> enum </h3>
```c
enum {CLUBS, DIAMONDS, HEARTS, SPADES} s1, s2;
enum suit {CLUBS, DIAMONDS, HEARTS, SPADES};
typedef enum {CLUBS, DIAMONDS, HEARTS, SPADES} Suit;
```
