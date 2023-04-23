The runtime stacks grow downwards from highest memory address to lower

You use a negative offset to allocate memory for a stack since it grows downwards
To allocate space for 3 registers:
```mips
addi $sp, $sp, -12
```


The heap grows upwards


### $la and $lw

$la is like the address of operator

$lw is like dereferencing a pointer 