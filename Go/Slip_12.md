# Go Lab Solutions

---

# Q1: Swap Two Numbers Using Call by Reference (Pointers)

## main.go

```go
// Swap call by reference
package main

import f "fmt"

// swap exchanges the values of x and y using pointers (call by reference)
func swap(x, y *int) {
	*x, *y = *y, *x
}

// Entry point: reads two numbers, swaps them, and displays results
func main() {
    var a, b int
    f.Print("Enter 2 numbers: ")
    f.Scan(&a, &b)
    f.Println("Original a: ", a, "\tb:", b)
    swap(&a, &b)
    f.Println("Swapped a: ", a, "\tb:", b)
}
```
