# 📝 Variables

- [📝 Variables](#-variables)
  - [👀 Fast Lookup](#-fast-lookup)
  - [📋 Declaring Variables](#-declaring-variables)
  - [📊 Types](#-types)
  - [🔄 Default Values](#-default-values)
  - [🔁 Type Conversion](#-type-conversion)

## 👀 Fast Lookup

- **Declaration**: `var name type` or `var name type = value`
- **Short declaration**: `name := value` (type inferred, function scope only)
- **Zero values**: Variables get zero values if not initialized
- **Strongly typed**: Must explicitly convert between types
- **Type conversion**: `int(floatVar)` to convert types
- **Numeric types**: int8/16/32/64, uint8/16/32/64, float32/64, complex64/128
- **Special types**: `byte` (uint8), `rune` (int32 for UTF-8)
- **Platform dependent**: `int` and `uint` size depends on platform

## 📋 Declaring Variables

```go
var num1 int; // Declare a variable without initialization (zero value will be assigned)
var name1 string = "John Doe" // Declare a variable with initialization

// Short variable declaration (abbreviation for var num2 int = 42)
num2 := 42 // (compiler infers the type)
```

## 📊 Types

- **Numeric types**
  - uint8, uint16, uint32, uint64
  - int8, int16, int32, int64
  - float32, float64
  - complex64, complex128
  - byte (alias for uint8)
  - rune (alias for int32, represents a single UTF-8 code point)
  - uint, int (platform-dependent size)

- **Other types**
  - Boolean (`true` or `false`)
  - String
  - Array (fixed-size sequence of elements of the same type)
  - Slice (array with dynamic size)
  - Struct (user-defined type)
  - Pointer (memory address of a variable)
  - Function Type (function pointer)
  - Interface (set of methods)
  - Map (key-value store)
  - Channel (queue type for concurrent programming)

## 🔄 Default Values

- Numeric types: `0`
- Boolean: `false`
- String: `""` (empty string)
- Other types: `nil` (Go keyword indicating an uninitialized memory address)

## 🔁 Type Conversion

> Go is strongly typed, meaning that variables must be explicitly converted between types when needed. Otherwise, the compiler will raise an error.

```go
a := 42
var b float64 = 3.5

var c int = b // Error: cannot use b (type float64) as type int in assignment
d := a * b    // Error: cannot perform operation between different types

// To convert types, use the type name as a function:
var e int = int(b)
f := a * int(b)
```
