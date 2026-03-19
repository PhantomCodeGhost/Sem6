# Go Lab Solutions

---

# Q1: Copy Array Elements Using a Method

## main.go

```go
package main

import "fmt"

// copyArray copies all elements from source to a new destination array and returns it
func copyArray(source [5]int) [5]int {
    var destination [5]int

    for i := 0; i < len(source); i++ {
        destination[i] = source[i]
    }

    return destination
}

// Entry point: demonstrates array copy using copyArray function
func main() {
    source := [5]int{10, 20, 30, 40, 50}

    // Call method
    destination := copyArray(source)

    fmt.Println("Source Array:", source)
    fmt.Println("Copied Array:", destination)
}
```
