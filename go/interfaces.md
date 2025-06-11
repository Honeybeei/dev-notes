# 🔌 Interfaces

- [🔌 Interfaces](#-interfaces)
  - [👀 Fast Lookup](#-fast-lookup)
  - [📋 Basic Syntax](#-basic-syntax)
  - [❓ Why use interfaces?](#-why-use-interfaces)
  - [🚀 Implicit Implementation](#-implicit-implementation)
  - [🔄 Polymorphism Example](#-polymorphism-example)
  - [🔳 Empty Interface](#-empty-interface)
  - [🔍 Type Assertion](#-type-assertion)
  - [🔀 Type Switches](#-type-switches)
  - [📚 Built-in Interfaces](#-built-in-interfaces)
    - [`fmt.Stringer`](#fmtstringer)
    - [`error` Interface](#error-interface)
    - [`io.Reader` and `io.Writer`](#ioreader-and-iowriter)
  - [📈 Interface Composition](#-interface-composition)
  - [⚠️ Interface Gotchas](#️-interface-gotchas)
    - [1. Nil Interface vs Nil Concrete Type](#1-nil-interface-vs-nil-concrete-type)
    - [2. Interface Satisfaction](#2-interface-satisfaction)
    - [3. Method Set Rules](#3-method-set-rules)

## 👀 Fast Lookup

- **Interface**: Set of method signatures that define behavior
- **Implicit implementation**: Types automatically implement interfaces if they have matching methods
- **Duck typing**: "If it walks like a duck and quacks like a duck, it's a duck"
- **Empty interface**: `interface{}` accepts any type (like `any` in newer versions)
- **Type assertion**: `value.(Type)` to convert interface to concrete type
- **Type switches**: `switch v := i.(type)` to handle multiple types
- **Polymorphism**: Same interface, different implementations
- **Decoupling**: Interfaces separate what something does from how it does it

## 📋 Basic Syntax

Interface is a set of methods

```go
type InterfaceName interface {
  Method1(args...) returnType
  // ...
}
```

## ❓ Why use interfaces?

- **Decoupling**: Interfaces separate what something does (behavior) from how it does it (implementation)
- **Polymorphism**: Different types can implement the same interface, allowing uniform treatment
- **Testing**: Easy to create mock implementations for testing
- **Flexibility**: Code can work with any type that implements the interface
- **API Design**: Define contracts without forcing specific implementations

## 🚀 Implicit Implementation

Go uses **implicit implementation** - types automatically implement interfaces if they have all the required methods. No explicit declaration needed!

```go
type Writer interface {
    Write([]byte) (int, error)
}

type File struct {
    name string
}

// File automatically implements Writer interface
func (f File) Write(data []byte) (int, error) {
    fmt.Printf("Writing to file %s: %s\n", f.name, data)
    return len(data), nil
}

func main() {
    var w Writer = File{name: "test.txt"}
    w.Write([]byte("Hello, World!"))
}
```

## 🔄 Polymorphism Example

```go
type Shape interface {
    Area() float64
    Perimeter() float64
}

type Circle struct {
    Radius float64
}

func (c Circle) Area() float64 {
    return 3.14159 * c.Radius * c.Radius
}

func (c Circle) Perimeter() float64 {
    return 2 * 3.14159 * c.Radius
}

type Rectangle struct {
    Width, Height float64
}

func (r Rectangle) Area() float64 {
    return r.Width * r.Height
}

func (r Rectangle) Perimeter() float64 {
    return 2 * (r.Width + r.Height)
}

// Function that works with any Shape
func PrintShapeInfo(s Shape) {
    fmt.Printf("Area: %.2f, Perimeter: %.2f\n", s.Area(), s.Perimeter())
}

func main() {
    circle := Circle{Radius: 5}
    rectangle := Rectangle{Width: 4, Height: 6}
    
    PrintShapeInfo(circle)    // Works with Circle
    PrintShapeInfo(rectangle) // Works with Rectangle
}
```

## 🔳 Empty Interface

The empty interface `interface{}` can hold any type (like `Object` in other languages):

```go
func PrintAnything(value interface{}) {
    fmt.Println(value)
}

func main() {
    PrintAnything(42)
    PrintAnything("hello")
    PrintAnything([]int{1, 2, 3})
    PrintAnything(map[string]int{"key": 123})
}
```

**Go 1.18+**: Use `any` instead of `interface{}`:

```go
func PrintAnything(value any) {
    fmt.Println(value)
}
```

## 🔍 Type Assertion

Extract the concrete type from an interface:

```go
func ProcessValue(value interface{}) {
    // Type assertion with ok pattern (safe)
    if str, ok := value.(string); ok {
        fmt.Printf("It's a string: %s\n", str)
    } else if num, ok := value.(int); ok {
        fmt.Printf("It's an int: %d\n", num)
    } else {
        fmt.Println("Unknown type")
    }
    
    // Direct type assertion (can panic if wrong type)
    // str := value.(string) // Panics if value is not a string
}

func main() {
    ProcessValue("hello")
    ProcessValue(42)
    ProcessValue(3.14)
}
```

## 🔀 Type Switches

Handle multiple types elegantly:

```go
func DescribeType(value interface{}) {
    switch v := value.(type) {
    case string:
        fmt.Printf("String of length %d: %s\n", len(v), v)
    case int:
        fmt.Printf("Integer: %d\n", v)
    case float64:
        fmt.Printf("Float: %.2f\n", v)
    case []int:
        fmt.Printf("Slice of ints with %d elements\n", len(v))
    case nil:
        fmt.Println("It's nil!")
    default:
        fmt.Printf("Unknown type: %T\n", v)
    }
}

func main() {
    DescribeType("hello")
    DescribeType(42)
    DescribeType(3.14)
    DescribeType([]int{1, 2, 3})
    DescribeType(nil)
}
```

## 📚 Built-in Interfaces

Go has many useful built-in interfaces:

### `fmt.Stringer`

```go
type Stringer interface {
    String() string
}

type Person struct {
    Name string
    Age  int
}

func (p Person) String() string {
    return fmt.Sprintf("%s (%d years old)", p.Name, p.Age)
}

func main() {
    person := Person{Name: "Alice", Age: 30}
    fmt.Println(person) // Automatically calls String() method
}
```

### `error` Interface

```go
type error interface {
    Error() string
}

type CustomError struct {
    Message string
    Code    int
}

func (e CustomError) Error() string {
    return fmt.Sprintf("Error %d: %s", e.Code, e.Message)
}

func DoSomething() error {
    return CustomError{Message: "Something went wrong", Code: 500}
}
```

### `io.Reader` and `io.Writer`

```go
type Reader interface {
    Read([]byte) (int, error)
}

type Writer interface {
    Write([]byte) (int, error)
}

// Many types implement these: files, network connections, buffers, etc.
```

## 📈 Interface Composition

Interfaces can embed other interfaces:

```go
type Reader interface {
    Read([]byte) (int, error)
}

type Writer interface {
    Write([]byte) (int, error)
}

type Closer interface {
    Close() error
}

// Composed interface
type ReadWriteCloser interface {
    Reader
    Writer
    Closer
}

// Or inline
type ReadWriter interface {
    Read([]byte) (int, error)
    Write([]byte) (int, error)
}
```

## ⚠️ Interface Gotchas

### 1. Nil Interface vs Nil Concrete Type

```go
func main() {
    var w io.Writer
    fmt.Println(w == nil) // true
    
    var f *os.File
    w = f
    fmt.Println(w == nil) // false! (interface contains (*os.File, nil))
    fmt.Println(f == nil) // true
}
```

### 2. Interface Satisfaction

```go
type MyInt int

func (m MyInt) String() string {
    return fmt.Sprintf("MyInt: %d", m)
}

func main() {
    var s fmt.Stringer = MyInt(42) // MyInt implements Stringer
    fmt.Println(s)
}
```

### 3. Method Set Rules

```go
type Counter struct {
    count int
}

func (c *Counter) Increment() { c.count++ }
func (c Counter) Value() int  { return c.count }

type Incrementer interface {
    Increment()
}

func main() {
    var inc Incrementer
    
    c := Counter{}
    // inc = c     // Error! Counter doesn't implement Incrementer
    inc = &c       // OK! *Counter implements Incrementer
    
    inc.Increment()
}
```
