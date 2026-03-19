# Go Lab Solutions

---

# Q1: Accept User Choice and Perform Arithmetic Operations

## main.go

```go
package main

import (
	f "fmt"
	"os"
)

// Entry point: reads two numbers and performs arithmetic based on user's menu choice
func main() {
	var a, b int
	f.Print("Enter num1 : ")
	f.Scan(&a)
	f.Print("Enter num2 : ")
	f.Scan(&b)

	var choice string

	// Continuously display menu until user chooses to exit
	for {
		f.Print("\nMenu:\n 1.Addition(+)\n 2.Subtraction(-)\n 3.Multiplication(*)\n 4.Division (/)\n 5.Exit(x)\n Enter your choice (+,-,*,/,x) : ")
		f.Scan(&choice)

		// Perform operation based on user's choice
		switch choice {

		case "+":
			f.Println("Addition :", a+b)

		case "-":
			f.Println("Subtraction :", a-b)

		case "*":
			f.Println("Multiplication :", a*b)

		case "/":
			f.Println("Division :", a/b)

		case "x":
			f.Println("Exiting....")
			os.Exit(0)

		default:
			f.Println("Enter valid choice (+,-,*,/,x)")
		}
	}
}
```
