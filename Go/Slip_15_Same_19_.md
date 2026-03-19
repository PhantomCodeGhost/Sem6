# Go Lab Solutions

---

# Q1: Demonstrate a Function Returning Multiple Values

## main.go

```go
package main

import "fmt"

// Function that returns sum and product of two numbers
func sum&sub(a, b int) (int, int) {
	return a + b, a - b
}

// Entry point: calls sum&sub and displays both return values
func main() {
	x, y := 5, 10

	// Call the function and get multiple return values
	sum, sub := sum&sub(x, y)

	fmt.Println("Sum:", sum)
	fmt.Println("Subtract:", sub)
}
```
