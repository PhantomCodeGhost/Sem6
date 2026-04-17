# Go Lab Solutions

---

# Q1: Print Multiplication Table of a Number Using a Function

## main.go

```go
package main
import f "fmt"

func table(n int) {
	
	for i:=1; i<11; i++{
	f.Println(n ," x ", i ," = ", n * i)
	}

}

func main(){
	var n int
	f.Print("Enter a number: ")
	f.Scan(&n)
	table(n)
}

```
