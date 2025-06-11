# 👉 Pointers

- [👉 Pointers](#-pointers)
  - [👀 Fast Lookup](#-fast-lookup)
  - [📈 Extra notes](#-extra-notes)

## 👀 Fast Lookup

- **Pointer**: Variable that stores memory address of another variable
- **Address operator**: `&variable` gets the address of a variable
- **Dereference operator**: `*pointer` gets the value at the address
- **Declaration**: `var p *int` declares a pointer to int
- **Zero value**: `nil` is the zero value of a pointer
- **Memory efficiency**: Pass large structs by pointer to avoid copying
- **Modification**: Pointers allow functions to modify original values
- **Safety**: Go doesn't allow pointer arithmetic (unlike C/C++)

Pointer is a variable that stores the memory address of another variable.

```go
var a int = 10
var b *int = &a // b stores the memory address of a

fmt.Println(a) // 10
fmt.Println(b) // memory address of a
fmt.Println(*b) // 10

*b = 20 // change the value of a. Assign 20 to the place where b points to
fmt.Println(a) // 20
```

## 📈 Extra notes

- `nil` is a zero value of a pointer.

- Q: Why use pointers?

```go
type Data struct {
  value int
  data [1000]float64
}

func DummyFunc1(data Data) {
  // When data is passed to the function, a copy of the data is created.
}

func DummyFunc2(data *Data) {
  // When pointer is passed to the function, the original data is passed.
  // Which means the function can modify the original data.
  // Also means the Data is not copied to the function. 
}
```
