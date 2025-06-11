# ⚙️ Methods

- [⚙️ Methods](#️-methods)
  - [👀 Fast Lookup](#-fast-lookup)
  - [🔄 Value Receiver vs Pointer Receiver](#-value-receiver-vs-pointer-receiver)

## 👀 Fast Lookup

- **Methods**: Functions associated with a specific type
- **Receiver**: `func (r Type) methodName()` - the type the method belongs to
- **Value receiver**: `func (r Type)` - works with copy of value
- **Pointer receiver**: `func (r *Type)` - works with original value
- **Modification rule**: Use pointer receiver to modify the original value
- **Performance**: Pointer receivers avoid copying large structs
- **Consistency**: If any method uses pointer receiver, all should for consistency
- **Method set**: Value and pointer types have different method sets

Methods are functions that are associated with a type.

basic syntax is:

```go
func (receiverType receiverName) methodName(parameters) (returnType) {
    // method body
}
```

```go
type Rectangle struct {
    Width  int
    Height int
}

func (r Rectangle) Area() int {
    return r.Width * r.Height
}
```

## 🔄 Value Receiver vs Pointer Receiver

- **Value receiver**: a copy of the value is passed to the method.
  - It's like static method in other languages. (not exact)
- **Pointer receiver**: the memory address of the value is passed to the method.
- **Recommendation**: use pointer receiver when you want to modify the original value.

```go
package main

import "fmt"

type account struct {
  balance int
}

func (a account) withdrawValue(amount int) {
  a.balance -= amount
}

func (a *account) withdrawPointer(amount int) {
  a.balance -= amount
}

func main() {
  account1 := &account{balance: 100}
  account1.withdrawValue(10)
  fmt.Println(account1.balance) // 100; no change
  account1.withdrawPointer(10)
  fmt.Println(account1.balance) // 90; changed
}

```
