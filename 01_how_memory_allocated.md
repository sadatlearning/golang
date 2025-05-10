## Understanding how memory is allocated in Go 

 - When functions are called is essential for writing performant and correct Go code.
 - Let's break this down carefully:
---
## 🔍 Function Calls & Memory Allocation in Go
### ✅ 1. **Function Itself: Code (Text) Segment**
When you define a function in Go:

```go
func greet() {
    fmt.Println("Hello!")
}
```

* The **function code** (its compiled machine instructions) is stored in the **code segment** (also called the *text segment*), **not** in heap or stack.
* This memory is **read-only and shared** among all goroutines.

---

### ✅ 2. **Local Variables in Functions: Stack vs Heap**

When a function is called, its **local variables** (e.g., variables declared inside the function) are:

* **Preferentially allocated on the stack** — because stack allocation is faster and automatically managed.
* But **can be "escaped" to the heap** if needed — depending on how they are used.

#### 🧠 Escape Analysis

Go uses **escape analysis** at compile time to decide **whether a variable should live on the stack or be moved to the heap**.

#### 🔍 Example 1: Stack Allocation (safe)

```go
func foo() int {
    x := 42
    return x
}
```

* Here, `x` is a local variable.
* It does **not escape** the function.
* So it is allocated on the **stack**.

#### 🔍 Example 2: Heap Allocation (escaped variable)

```go
func foo() *int {
    x := 42
    return &x
}
```

* `x` is **referenced** and returned outside the function.
* `x` must outlive the function’s stack frame.
* So `x` is **allocated on the heap**.

The compiler sees that `x` "escapes" the function and uses the **heap** instead of the **stack**.

---

### ✅ 3. **Stack Memory in Go**

* Go uses a **split stack** model.
* Each goroutine starts with a small stack (e.g., 2KB) that **grows and shrinks dynamically**.
* This differs from C/C++ where stack size is fixed per thread.

---

### ✅ 4. **Heap Memory in Go**

* Used for long-lived objects or those whose lifetimes exceed the stack frame.
* Managed by Go’s **garbage collector**.
* Variables that **escape the local scope** are allocated on the **heap**.

---

### ✅ 5. Summary Table

| Memory Location | Used For                         | Automatically Freed? | Managed By        |
| --------------- | -------------------------------- | -------------------- | ----------------- |
| Stack           | Local non-escaping variables     | Yes (at return)      | Go runtime        |
| Heap            | Escaping variables, global state | No (GC required)     | Garbage Collector |
| Text Segment    | Function code itself             | Static               | OS loader/runtime |

---

### ✅ 6. How to See Stack vs Heap Allocation?

Use Go’s **escape analysis tool**:

```bash
go build -gcflags="-m" main.go
```

This will show which variables are allocated to the heap and which to the stack.

---
