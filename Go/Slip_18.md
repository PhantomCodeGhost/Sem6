# Go Lab Solutions

---

# Q1: Print Multiplication Table of a Number Using a Function

## main.go

```go
package main

import f "fmt"

// Entry point: reads a number and prints its multiplication table from 1 to 10
func main() {
    var n int
    f.Print("Enter a number: ")
    f.Scanln(&n)

    // Print multiplication table from 1 to 10
    for i := 1; i <= 10; i++ {
        f.Println(n, "x", i, "=", n*i)
    }
}
```
