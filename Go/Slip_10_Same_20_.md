# Go Lab Solutions

---

# Q1: Read and Write Fibonacci Series Using a Channel
# Q2: Create a Channel and Illustrate Closing It Using `for range` and `close`

> **Note:** Both Q1 and Q2 are solved by the same program below, which demonstrates
> sending Fibonacci values through a channel and closing it after all values are sent.

## main.go

```go
package main

import f "fmt"

// fibonacci sends n Fibonacci numbers into the channel, then closes it
func fibonacci(n int, ch chan int) {
	a, b := 0, 1
	for i := 0; i < n; i++ {
		ch <- a // send value to channel
		a, b = b, a+b
	}
	close(ch) // close channel after sending all values
}

// Entry point: launches a goroutine to generate Fibonacci numbers and reads them via channel
func main() {
	var num int
	f.Print("How many terms? ")
	f.Scan(&num)

	ch := make(chan int)

	// Start goroutine to generate Fibonacci numbers
	go fibonacci(num, ch)

	f.Println("Fibonacci series:")
	// Receive values from channel until it is closed
	for val := range ch {
		f.Print(val, "\t")
	}
}
```
