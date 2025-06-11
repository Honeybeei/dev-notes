# 🏗️ Structs

- [🏗️ Structs](#️-structs)
  - [👀 Fast Lookup](#-fast-lookup)
  - [📋 Declaring and Initializing Structs](#-declaring-and-initializing-structs)
  - [🔍 Accessing Structs](#-accessing-structs)
  - [⚙️ Creating Instance of Struct](#️-creating-instance-of-struct)

## 👀 Fast Lookup

- **Struct**: User-defined type that groups variables of different types
- **Field access**: Use dot notation `struct.field` to access fields
- **Zero value**: Uninitialized structs get zero values for all fields
- **Literal initialization**: `Person{Name: "John", Age: 25}` with field names
- **Positional initialization**: `Person{"John", 25}` without field names (order matters)
- **Pointer creation**: `&Person{}` creates pointer to struct
- **`new()` function**: `new(Person)` creates pointer to zero-valued struct
- **Value vs pointer**: Structs can be passed by value or reference

Struct is a user-defined data type that groups variables of different data types.

```go
type StructName struct {
  Field1Type Field1Name
  Field2Type Field2Name
  // ...
}
```

## 📋 Declaring and Initializing Structs

```go
type Person struct {
    Name string
    Age int
    IsStudent bool
}

var person1 Person // Zero value initialization

// Struct literal initialization with field names
person2 := Person{
    Name: "John Doe",
    Age: 25,
    IsStudent: true,
}

// Struct literal initialization without field names
person3 := Person{"Jane Doe", 23, false}
```

## 🔍 Accessing Structs

```go
person2.Name = "John Doe"
person2.Age = 25
person2.IsStudent = true
```

## ⚙️ Creating Instance of Struct

```go
type Student struct {
  name string
  age int
}

func main() {
  // Create a new instance of Student with initial values
  var s1 *Student = &Student{name: "John", age: 25}
  s2 := &Student{} // Zero value initialization

  // Using new() function
  s3 := new(Student)
}
```
