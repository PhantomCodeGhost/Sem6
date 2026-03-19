# Go Lab Solutions

---

# Q1: Check Whether the Accepted Number is a Two-Digit Number or Not

## main.go

```go
package main

import f "fmt"

// Entry point: reads a number and checks if it is a two-digit number
func main() {
	var num int
	f.Print("Enter a number: ")
	f.Scan(&num)

	// Check for two-digit range for both positive and negative numbers
	if num >= 10 && num <= 99 || num <= -10 && num >= -99 {
		f.Println(num, "is a two-digit number.")
	} else {
		f.Println(num, "is not a two-digit number.")
	}
}
```
