# 🔤 Strings

- [🔤 Strings](#-strings)
  - [👀 Fast Lookup](#-fast-lookup)
  - [🌍 UTF-8](#-utf-8)
  - [🔍 Internal Structure of String](#-internal-structure-of-string)

## 👀 Fast Lookup

- **UTF-8 encoding**: Go strings use UTF-8, 1-4 bytes per character
- **`rune`**: Alias for `int32`, represents a single UTF-8 character
- **`len()` vs character count**: `len()` returns bytes, not character count
- **Character count**: Use `len([]rune(str))` to get actual character count
- **Range iteration**: Use `range` to iterate over runes, not bytes
- **Immutable**: Strings are read-only slices of bytes
- **Internal structure**: String = pointer + length (like slice header)
- **Copy behavior**: Copying strings copies pointer and length, not underlying bytes

In this note, I will just list down the things I need to remember about strings in Go.

## 🌍 UTF-8

- Go use "UTF-8" encoding for strings. And a single UTF-8 needs 1 to 4 bytes to represent.
  - Go use `rune` (alias for `int32`) to represent a single character in a string.
- `len()` returns the number of bytes in a string.
- To get the number of actual characters in a string, use `[]rune` to convert the string to a slice of runes.

```go
func main() {
  str := "안녕, World!"
  fmt.Println(len(str)) // 12
  fmt.Println(len([]rune(str))) // 11
}
```

- To iterate over a string, use `range` instead of `len()`.

```go
func main() {
  str := "안녕, World!"
  for i, r := range str {
    fmt.Println(i, r)
  }
}
```

## 🔍 Internal Structure of String

- String in Go is a read-only (immutable) slice of bytes.
  - "read-only" means the bytes cannot be modified.

```go
type StringHeader struct {
  Data uintptr
  Len int
}
```

- String is basically pointer and length.
- Which means when a string is copied, pointer and length are copied.
- Which means the copied string will also point to the same underlying bytes.
