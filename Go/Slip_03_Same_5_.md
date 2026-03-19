# Go Lab Solutions

---

# Q1: Accept N Employee Records and Display Employee with Maximum Salary

## main.go

```go
package main

import "fmt"

// Employee holds employee number, name, and salary
type Employee struct {
    no     int
    name   string
    salary int
}

// Entry point: reads n employee records and prints the one with the highest salary
func main() {
    var n int
    fmt.Print("How many employees? ")
    fmt.Scan(&n)

    employees := make([]Employee, n)

    // Read employee details
    for i := 0; i < n; i++ {
        fmt.Println("Employee", i+1)
        fmt.Print("Enter Employee no: ")
        fmt.Scan(&employees[i].no)
        fmt.Print("Enter Employee name: ")
        fmt.Scan(&employees[i].name)
        fmt.Print("Enter salary: ")
        fmt.Scan(&employees[i].salary)
        fmt.Println()
    }

    // Display all employee records
    for i := 0; i < n; i++ {
        fmt.Println("Details of Employee", i+1)
        fmt.Println(employees[i].no, employees[i].name, employees[i].salary)
    }

    // Find max salary
    maxIndex := 0
    for i := 1; i < n; i++ {
        if employees[i].salary > employees[maxIndex].salary {
            maxIndex = i
        }
    }

    fmt.Println("\nMax Salary Employee:")
    fmt.Println(employees[maxIndex].no, employees[maxIndex].name, employees[maxIndex].salary)
}
```

---

# Q2: Accept N Employee Records and Display Employee with Minimum Salary

## main.go

```go
package main

import "fmt"

// Employee holds employee number, name, and salary
type Employee struct {
    no     int
    name   string
    salary int
}

// Entry point: reads n employee records and prints the one with the lowest salary
func main() {
    var n int
    fmt.Print("How many employees? ")
    fmt.Scan(&n)

    employees := make([]Employee, n)

    // Read employee details
    for i := 0; i < n; i++ {
        fmt.Println("Employee", i+1)
        fmt.Print("Enter Employee no: ")
        fmt.Scan(&employees[i].no)
        fmt.Print("Enter Employee name: ")
        fmt.Scan(&employees[i].name)
        fmt.Print("Enter salary: ")
        fmt.Scan(&employees[i].salary)
        fmt.Println()
    }

    // Display all employee records
    for i := 0; i < n; i++ {
        fmt.Println("Details of Employee", i+1)
        fmt.Println(employees[i].no, employees[i].name, employees[i].salary)
    }

    // Find minimum salary
    minIndex := 0
    for i := 1; i < n; i++ {
        if employees[i].salary < employees[minIndex].salary {
            minIndex = i
        }
    }

    fmt.Println("\nMin Salary Employee:")
    fmt.Println(employees[minIndex].no, employees[minIndex].name, employees[minIndex].salary)
}
```
