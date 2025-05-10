## **Go (Golang) Cheat Sheet** designed to get you productive from the **fundamentals** upward — ideal for quick reference and learning.

---

## 🟢 Go (Golang) Cheat Sheet — Fundamental Level

### ✅ 1. Hello World

```go
package main
import "fmt"

func main() {
    fmt.Println("Hello, World!")
}
```

---

### ✅ 2. Variables & Constants

```go
var x int = 10
y := 20 // short declaration

const Pi = 3.14
```

---

### ✅ 3. Data Types

```go
// Integer
var i int = 42

// Float
var f float64 = 3.14

// Boolean
var isGoFun bool = true

// String
var name string = "Go"
```

---

### ✅ 4. Functions

```go
func add(a int, b int) int {
    return a + b
}
```

---

### ✅ 5. Control Structures

```go
// if-else
if x > 10 {
    fmt.Println("Big")
} else {
    fmt.Println("Small")
}

// switch
switch x {
case 1:
    fmt.Println("One")
default:
    fmt.Println("Other")
}
```

---

### ✅ 6. Loops

```go
for i := 0; i < 5; i++ {
    fmt.Println(i)
}

// while-like
i := 0
for i < 5 {
    fmt.Println(i)
    i++
}
```

---

### ✅ 7. Arrays & Slices

```go
arr := [3]int{1, 2, 3}
slice := []int{4, 5, 6}
slice = append(slice, 7)
```

---

### ✅ 8. Maps (Dictionaries)

```go
m := map[string]int{"apple": 1, "banana": 2}
fmt.Println(m["apple"])
```

---

### ✅ 9. Structs

```go
type Person struct {
    Name string
    Age  int
}

p := Person{Name: "Alice", Age: 30}
fmt.Println(p.Name)
```

---

### ✅ 10. Pointers

```go
x := 10
p := &x
fmt.Println(*p) // dereference
```

---

### ✅ 11. Interfaces

```go
type Speaker interface {
    Speak()
}

type Dog struct{}

func (d Dog) Speak() {
    fmt.Println("Woof!")
}
```

---

### ✅ 12. Goroutines & Channels

```go
// Goroutine
go func() {
    fmt.Println("Running in background")
}()

// Channel
ch := make(chan int)
go func() {
    ch <- 42
}()
fmt.Println(<-ch)
```

---

### ✅ 13. Error Handling

```go
val, err := strconv.Atoi("42")
if err != nil {
    fmt.Println("Error:", err)
}
```

---

### ✅ 14. File I/O (basic)

```go
data, err := os.ReadFile("file.txt")
if err == nil {
    fmt.Println(string(data))
}
```

---

### ✅ 15. Useful Commands

| Command                  | Description             |
| ------------------------ | ----------------------- |
| `go run file.go`         | Run a Go file           |
| `go build`               | Compile current package |
| `go build -o out.exe`    | Build and name output   |
| `go fmt`                 | Format code             |
| `go mod init modulename` | Initialize Go module    |
| `go get pkg`             | Install a package       |
| `go test`                | Run tests               |
