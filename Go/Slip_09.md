# Go Lab Solutions

---

# Q1: Check Whether an Accepted Number is a Palindrome or Not

## main.go

```go
package main

import f "fmt"

// Palindrome checks if the given number reads the same forwards and backwards
func Palindrome(n int) string {
    tmp := n
    rev := 0

    // Reverse the digits of n
    for n > 0 {
        rem := n % 10
        rev = rev*10 + rem
        n = n / 10
    }

    if rev == tmp {
        return " is a Palindrome!!"
    } else {
        return " is NOT a Palindrome!!"
    }
}

// Entry point: reads a number and prints palindrome check result
func main() {
    var a int
    f.Print("Enter a number: ")
    f.Scan(&a)
    f.Print(a, Palindrome(a))
}
```
