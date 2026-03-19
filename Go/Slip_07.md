# Go Lab Solutions

---

# Q1: Accept a Matrix and Display Its Transpose

## main.go

```go
package main

import f "fmt"

// Entry point: reads a matrix and displays its original and transposed forms
func main() {
    var r, c int

    f.Print("How many rows & columns? ")
    f.Scan(&r, &c)

    // Create matrix using a 2D slice
    mat := make([][]int, r)
    for i := range mat {
        mat[i] = make([]int, c)
    }

    // Input elements
    f.Println("Enter elements of matrix:")
    for i := range mat {
        for j := range mat[i] {
            f.Scan(&mat[i][j])
        }
    }

    // Display original matrix
    f.Println("\nOriginal Matrix:")
    for i := range mat {
        for j := range mat[i] {
            f.Print(mat[i][j], "\t")
        }
        f.Println()
    }

    // Display transpose by swapping row and column indices
    f.Println("\nTranspose Matrix:")
    for i := 0; i < c; i++ {
        for j := 0; j < r; j++ {
            f.Print(mat[j][i], "\t")
        }
        f.Println()
    }
}
```
