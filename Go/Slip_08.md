# Go Lab Solutions

---

# Q1: Accept and Display Book Details for N Books

## main.go

```go
package main

import f "fmt"

// book holds details of a single book record
type book struct {
	bid    int
	title  string
	author string
	price  float32
}

// Entry point: reads n book records and displays all of them
func main() {
	var n int
	f.Print("How many books? ")
	f.Scan(&n)

	// Create a slice to hold n book records
	bk := make([]book, n)

	// Read details for each book
	for i := 0; i < n; i++ {
		f.Print("Enter bid, title, author, price = ")
		f.Scan(&bk[i].bid, &bk[i].title, &bk[i].author, &bk[i].price)
	}

	// Display all book records
	f.Println("\nBooks Details:")
	for i := 0; i < n; i++ {
		f.Println(bk[i].bid, bk[i].title, bk[i].author, bk[i].price)
	}
}
```
