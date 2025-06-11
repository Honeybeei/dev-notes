# 📊 Arrays

- [📊 Arrays](#-arrays)
  - [👀 Fast Lookup](#-fast-lookup)
  - [📋 Declaration and Initialization](#-declaration-and-initialization)
  - [🔍 Accessing and Looping](#-accessing-and-looping)
  - [📄 Copying](#-copying)

## 👀 Fast Lookup

- **Fixed size**: Arrays have a fixed size defined at compile time
- **Declaration**: `var arr [5]int` or `arr := [5]int{1,2,3,4,5}`
- **Size inference**: Use `[...]` to let compiler infer size: `arr := [...]int{1,2,3}`
- **Zero values**: Uninitialized elements get zero values of their type
- **Value semantics**: Arrays are copied by value, not reference
- **Type includes size**: `[3]int` and `[5]int` are different types
- **Range loop**: Use `for i, v := range arr` to iterate

## 📋 Declaration and Initialization

```go
// Without type inference
var days [7]string // ["", "", "", "", "", "", ""]

// With type inference
numArray1 := [5]int{1, 2, 3, 4, 5}

// With `...` to let the compiler infer the size
numArray2 := [...]{1, 2, 3} // compiler infers the size to be 3 and type to be int
```

## 🔍 Accessing and Looping

```go
days := [...]{"Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"}

// Accessing
days[0] // "Monday"
days[6] // "Sunday"

// Looping using len()
for i := 0; i < len(days); i++ {
    fmt.Println(days[i])
}

// Looping with range
for i, day := range days {
    fmt.Println(i, day)
}
```

## 📄 Copying

When an array is copied, a new array is created and the values are copied from the original array to the new array.

```go
arr1 := [3]int{1, 2, 3}
arr2 := arr1 // arr2 is a copy of arr1
arr2[0] = 100
fmt.Println(arr1) // [1, 2, 3]
fmt.Println(arr2) // [100, 2, 3]

var arr3 [3]float64
arr3 = arr1 // Error: cannot assign [3]int to [3]float64. Type must match. 
```
