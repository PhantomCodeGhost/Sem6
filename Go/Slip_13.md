# Go Lab Solutions

---

# Q1: Print Sum of All Even and Odd Numbers Separately Between 1 to 100

## main.go

```go
package main

import "fmt"

// Entry point: calculates and prints sum of even and odd numbers from 1 to 100
func main() {
	sumEven, sumOdd := 0, 0

	// Iterate from 1 to 100 and accumulate even and odd sums separately
	for i := 1; i <= 100; i++ {
		if i%2 == 0 {
			sumEven += i
		} else {
			sumOdd += i
		}
	}

	fmt.Println("Sum of even numbers:", sumEven)
	fmt.Println("Sum of odd numbers:", sumOdd)
}
```
