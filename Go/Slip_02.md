# Go Lab Solutions

---

# Q1: Print Fibonacci Series of N Terms

## main.go

```go
package main

import f "fmt"

// Entry point: reads number of terms and prints Fibonacci series
func main() {
    var num int
    f.Print("How many terms? ")
    f.Scan(&num)
    a, b := 0, 1

    // Generate and print Fibonacci terms iteratively
    for i := 0; i < num; i++ {
        f.Print(a, "\t")
        a, b = b, a+b
    }
}
```
