# Go Lab Solutions

---

# Q1: Copy Array Elements Using a Method

## main.go

```go
package main

import "fmt"

type Array struct {
	a [5]int
}

// Method
func (x Array) copyArray() [5]int {
	var destination [5]int

	for i := 0; i < len(x.a); i++ {
		destination[i] = x.a[i]
	}

	return destination
}

func main() {
	var obj Array
	obj.a = [5]int{10, 20, 30, 40, 50}

	destination := obj.copyArray()

	fmt.Println("Source Array:", obj.a)
	fmt.Println("Copied Array:", destination)
}
```
