# 🧾 GO VIVA – FINAL REVISION SHEET (Topper Level)

---

## 🔥 1. FUNDAMENTALS (ALWAYS ASKED)

### Q1. What is Go?
→ Compiled, statically typed language designed for concurrency and performance.

### Q2. Why Go is faster than Python?
→ Go is compiled; Python is interpreted.

### Q3. Entry point of Go program?
→ `package main` and `func main()`

### Q4. What is := ?
→ Short variable declaration (only inside functions)

### Q5. What is zero value?
→ Default value (int=0, string="", bool=false)

### Q6. fmt.Println vs fmt.Printf
→ Println: simple output  
→ Printf: formatted output

---

## ⚡ 2. CORE CONCEPTS (VERY IMPORTANT)

---

### 🔹 Array vs Slice (MOST IMPORTANT)

| Feature | Array | Slice |
|--------|------|------|
| Size | Fixed | Dynamic |
| Type | Value type | Reference type |
| Memory | Full copy | Points to underlying array |

✔️ Slice = pointer + length + capacity  
✔️ Slice internally uses array  

---

### 🔹 Slice Internals

### Q. Length vs Capacity?
→ Length = number of elements  
→ Capacity = max size before reallocation  

### Q. What happens when capacity exceeds?
→ New array created, elements copied  

---

### 🔹 Pass by Value

### Q. How Go passes variables?
→ Always pass by value  

### Q. Why slices modify original data?
→ Because slice references underlying array  

---

### 🔹 Function vs Method

| Function | Method |
|---------|--------|
| Independent | Attached to type |
| No receiver | Has receiver |

✔️ Method = Function + Receiver  

---

### 🔹 Pointer

### Q. What is pointer?
→ Stores memory address  

### Q. Why use pointer?
→ Modify original data, avoid copying  

---

### 🔹 Struct

### Q. What is struct?
→ User-defined type grouping variables  

### Q. Why use struct?
→ Organize related data  

---

### 🔹 Interface (Conceptual)

### Q. What is interface?
→ Defines method signatures  

### Q. Empty interface?
→ `interface{}` holds any type  

---

## 🔁 3. CONCURRENCY (HIGH WEIGHTAGE)

---

### 🔹 Goroutine

### Q. What is goroutine?
→ Lightweight thread managed by Go runtime  

### Q. How to create?
→ Use `go` keyword  

---

### 🔹 Channel

### Q. What is channel?
→ Communication between goroutines  

### Q. Syntax?
→ `ch := make(chan int)`  

---

### 🔹 Buffered vs Unbuffered

| Unbuffered | Buffered |
|-----------|----------|
| Blocking | Limited non-blocking |
| Sync | Async possible |

---

### 🔹 close() and range

### Q. Why close channel?
→ Indicate no more values  

### Q. range over channel?
→ Runs until channel is closed  

---

## 🔁 4. PROGRAM-BASED (FROM YOUR REPO)

---

### 🔹 Fibonacci

→ Logic: `a, b = b, a+b`  
✔️ Iterative is efficient  

---

### 🔹 Recursion

→ Function calls itself  
✔️ Needs base condition  
❌ Risk: stack overflow  

---

### 🔹 Struct + Method

→ Method attached to struct  
✔️ Organizes logic  

---

### 🔹 Array Copy

→ Loop copy  
✔️ Arrays are value types  

✔️ “Copy creates independent array”  

---

### 🔹 Switch Case

→ Cleaner than if-else ladder  

---

## 🧠 5. PREVIOUS / IMPORTANT VIVA QUESTIONS

---

### Q. What is method in Go?
→ Function with receiver  

### Q. Why struct required for method?
→ Methods are defined on types  

### Q. What is goroutine?
→ Lightweight thread  

### Q. What is channel?
→ Communication between goroutines  

### Q. What is close()?
→ Stops sending values  

---

## 🎯 6. TRICK / CONCEPTUAL QUESTIONS

---

### Q. Can array be modified in function?
→ ❌ No (pass by value)  

### Q. How to modify original data?
→ Use pointer or slice  

### Q. Why no inheritance in Go?
→ Uses composition  

### Q. What if variable unused?
→ Compilation error  

### Q. Multiple return values?
→ ✅ Supported  

---

### 🔹 Stack vs Heap

| Stack | Heap |
|------|------|
| Fast | Slower |
| Fixed | Dynamic |

---

### Q. What is garbage collection?
→ Automatic memory management  

---


✔️ Go always passes values, slices behave like references  
✔️ Slice is descriptor of underlying array  
✔️ Concurrency uses goroutines and channels  
✔️ Go uses composition, not inheritance  
✔️ Slices preferred over arrays  

---

## ✅ 8. FINAL CHECKLIST

- Array vs Slice (with internals)  
- Pass by value  
- Pointer basics  
- Method vs Function  
- Struct  
- Goroutine & Channel  
- Recursion  
- Fibonacci logic  

---

## ⚡ TL;DR

- Go = Compiled + Concurrent  
- Slice = pointer + len + cap  
- Arrays copy, slices reference  
- Goroutines = lightweight threads  
- Channels = communication  
