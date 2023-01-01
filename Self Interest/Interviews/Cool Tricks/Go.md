## Associating a function to a type
	// (b bill) will associate the format function with the bill type
```go

func (b bill) format() string {
  // 
}
```

## If with a short statement
	// Like for, the if statement can start with a short statement to execute before the condition.

```go
if v := math.Pow(x, n); v < lim {
	return v
}
```