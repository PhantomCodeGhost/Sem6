# Go Lab Solutions

---

# Q1: Create a User-Defined Package to Find the Area of a Rectangle

## area.go
> **File path:** `C:\Program Files\Go\src\rectangle\area.go`

```go
// User defined package
package rectangle

// Area calculates and returns the area of a rectangle given length and width
func Area(length, width float64) float64 {
    return length * width
}
```

---

## My.go
> **File path:** `C:\Program Files\Go\My.go`

```go
package main

import (
    f "fmt"
    "rectangle" // simple local import
)

// Entry point: reads rectangle dimensions and prints the area using the rectangle package
func main() {
    var length, width float64

    f.Print("Enter length: ")
    f.Scanln(&length)

    f.Print("Enter width: ")
    f.Scanln(&width)

    area := rectangle.Area(length, width)
    f.Printf("The area of the rectangle is: %.2f\n", area)
}
```
