# Go Lab Solutions

---

# Q1: Demonstrate Working of Slices (append, remove, copy, iterate)

## main.go

```go
package main

import "fmt"

// Entry point: demonstrates common slice operations in Go
func main() {
	// Creating a slice
	slice := []int{10, 20, 30, 40, 50}
	fmt.Println("Original slice:", slice)

	// Append elements
	slice = append(slice, 60, 70)
	fmt.Println("After append:", slice)

	// Remove element at index 2 (value 30)
	index := 2
	slice = append(slice[:index], slice[index+1:]...)
	fmt.Println("After removing index 2:", slice)

	// Copy slice to a new slice
	newSlice := make([]int, len(slice))
	copy(newSlice, slice)
	fmt.Println("Copied slice:", newSlice)

	// Iterating over slice
	fmt.Print("Elements of slice: ")
	for _, val := range slice {
		fmt.Print(val, " ")
	}
	fmt.Println()
}
```
