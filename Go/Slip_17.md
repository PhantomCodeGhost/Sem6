# Go Lab Solutions

---

# Q1: Illustrate Returning Multiple Values from a Function (Add, Subtract, Multiply, Divide)

## main.go

```go
package main

import f "fmt"

// Calculate performs Add, Subtract, Multiply, Divide directly
// Returns 0 for division if b is zero to avoid division by zero panic
func Calculate(a, b float64) (float64, float64, float64, float64) {
    if b != 0 {
        return a + b, a - b, a * b, a / b
    }
    return a + b, a - b, a * b, 0 // division by zero handled
}

// Entry point: reads two numbers and displays all four arithmetic results
func main() {
    var num1, num2 float64

    f.Print("Enter first number: ")
    f.Scanln(&num1)

    f.Print("Enter second number: ")
    f.Scanln(&num2)

    add, sub, mul, div := Calculate(num1, num2)

    f.Printf("Addition: %.2f\n", add)
    f.Printf("Subtraction: %.2f\n", sub)
    f.Printf("Multiplication: %.2f\n", mul)

    // Error Handling
    if num2 != 0 {
        f.Printf("Division: %.2f\n", div)
    } else {
        f.Println("Division: Cannot divide by zero")
    }
}
```
