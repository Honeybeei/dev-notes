# 🔀 Control Flow

- [🔀 Control Flow](#-control-flow)
  - [👀 Fast Lookup](#-fast-lookup)
  - [❓ If-Else](#-if-else)
    - [📋 Basic Syntax](#-basic-syntax)
    - [⚙️ if Statement with Initializer and Condition](#️-if-statement-with-initializer-and-condition)
  - [🔀 Switch Statement](#-switch-statement)
    - [📋 Basic Syntax](#-basic-syntax-1)
    - [🔢 Switch Statement with Multiple Cases](#-switch-statement-with-multiple-cases)
    - [⚙️ Switch Statement with Initializer and Condition](#️-switch-statement-with-initializer-and-condition)
  - [🔁 for Loop](#-for-loop)
    - [🌍 for Loop with Range](#-for-loop-with-range)

## 👀 Fast Lookup

- **if with initializer**: `if init; condition { }` - init variable scoped to if block
- **switch**: No automatic fallthrough, can have multiple values per case
- **switch with initializer**: `switch init; expr { }` - init scoped to switch
- **for loop**: Only loop keyword in Go, multiple syntactic forms
- **range**: `for i, v := range collection` - iterates over collections
- **infinite loop**: `for { }` - loop without condition
- **while-style**: `for condition { }` - loop with only condition
- **Variable scoping**: Variables in init statements limited to block scope

## ❓ If-Else

### 📋 Basic Syntax

```go
if condition {
   // code to be executed if the condition is true
} else {
    // code to be executed if the condition is false
}
```

### ⚙️ if Statement with Initializer and Condition

This is bit tricker

```go
if initializerStatement; condition {
  // code to be executed if the condition is true
} else {
  // code to be executed if the condition is false
}
```

In the above example, the `initializerStatement` is executed before the `condition` is evaluated.

> !Important: The scope of variables declared in the initializer statement is limited to the if statement block. It cannot be accessed outside the block.

```go
if filename, err := UploadFile(); err == nil {
  fmt.Println("File uploaded successfully:", filename) // filename is accessible here
} else {
  fmt.Println(err) // err is accessible here
}

fmt.Println(filename, err) // filename and err are not accessible here
```

## 🔀 Switch Statement

### 📋 Basic Syntax

```go
switch expression {
  case value1: 
    // if expression == value1, execute this block
  case value2: 
    // if expression == value2, execute this block
  default: 
    // if expression doesn't match any case, execute this block
    // default is optional
}
```

### 🔢 Switch Statement with Multiple Cases

```go
switch expression {
  case value1, value2, value3: 
    // if expression == value1 or value2 or value3, execute this block
  default: 
    // if expression doesn't match any case, execute this block
}
```

### ⚙️ Switch Statement with Initializer and Condition

```go
switch initializerStatement; expression {
  case value1, value2, value3: 
    // if expression == value1 or value2 or value3, execute this block
  default: 
    // if expression doesn't match any case, execute this block
}
```

As like if statement, the scope of variables declared in the initializer statement is limited to the switch statement block.

## 🔁 for Loop

Go only has one loop keyword, `for`.

```go
for initializerStatement; condition; postStatement {
  // code to be executed
}
```

also there are other ways to use for loop

```go
// without initializerStatement
for ; condition; postStatement {
  // code to be executed
}

// without postStatement
for initializerStatement; condition; {
  // code to be executed
}

// without initializerStatement and postStatement
for condition {
  // code to be executed
}

// without condition
for {
  // code to be executed
}
```

### 🌍 for Loop with Range

Range is used to iterate over collections

```go
for index, value := range collection {
  // code to be executed
}

// without index
for _, value := range collection {
  // code to be executed
}

// without value
for index := range collection {
  // code to be executed
}

// without index and value
for range collection {
  // code to be executed
}
```
