# Go Lab Solutions

---

# Q1: Print Recursive Sum of Digits of a Given Number

## main.go

```go
package main

import f "fmt"

// rec_sum recursively calculates the sum of digits of num
func rec_sum(num int) int {
	if num == 0 {
		return 0
	} else {
		// Add last digit to recursive sum of remaining digits
		return (num % 10) + rec_sum(num/10)
	}
}

// Entry point: reads a number and prints its recursive digit sum
func main() {
	var n int
	f.Print("Enter a no : ")
	f.Scan(&n)
	f.Print("Recursive Sum : ", rec_sum(n))
}
```
