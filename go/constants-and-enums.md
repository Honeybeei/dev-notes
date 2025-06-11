# 🗿 Constants and Enum(`iota`)

- [🗿 Constants and Enum(`iota`)](#-constants-and-enumiota)
  - [👀 Fast Lookup](#-fast-lookup)
  - [🗿 Constants](#-constants)
  - [🔢 Enum in Go (`iota`)](#-enum-in-go-iota)
  - [📝 Constant and Literal](#-constant-and-literal)

## 👀 Fast Lookup

- **Constants**: Immutable values declared with `const` keyword
- **Primitive types only**: bool, numeric, string, rune can be constants
- **Compile-time evaluation**: Constants are evaluated at compile time
- **`iota`**: Special identifier for creating enums, starts at 0
- **Auto-increment**: `iota` increments automatically in const blocks
- **Custom types**: Define enum type like `type Status int`
- **String method**: Implement `String()` method for readable enum output
- **Type safety**: Enums provide type-safe constants

## 🗿 Constants

- The value of a constant cannot be changed once it is assigned.
  - Compiler will throw an error if you try to change the value of a constant.
- Only primitive types can be used as constants.
  - boolean
  - numeric (int, float, complex)
  - string and character
  - rune
- Constants are declared using `const` keyword.
- Constants can be declared without type specification as well.

## 🔢 Enum in Go (`iota`)

- The iota operator is used to generate unique integer constants for an enumeration.
- It starts from zero by default, but you can also specify the starting value of iota with a constant declaration.

```go
// 1. Define a custom type for the enum
type Status int

// 2. Declare constants using iota for the enum values
const (
  Pending Status = iota // 0
  Active                // 1 (iota increments automatically)
  Completed             // 2
  Failed                // 3
)

// Optional: String method for human-readable output (implements fmt.Stringer)
func (s Status) String() string {
  switch s {
  case Pending:
    return "Pending"
  case Active:
    return "Active"
  case Completed:
    return "Completed"
  case Failed:
    return "Failed"
  default:
    return "Unknown"
 }
}
```

## 📝 Constant and Literal

In Go, constants are treated as literal values, which means it will be evaluated at compile time.

```go
const PI = 3.14
var a int = PI * 100
```

After compilation, the statement `a = 314` will be executed.
