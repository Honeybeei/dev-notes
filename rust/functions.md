# 🔧 Functions

- [🔧 Functions](#-functions)
  - [👀 Fast Lookup](#-fast-lookup)
  - [📝 Statement and Expression](#-statement-and-expression)
  - [🏗️ Function Definition](#️-function-definition)

## 👀 Fast Lookup

- Use `fn` to define a function.
- Use **snake_case** for function names.
- Functions can return values using the last expression in the function body.

## 📝 Statement and Expression

- **Statements**: Instructions that perform an action and do not return a value.
- **Expressions**: Evaluate the result and can be part of a statement.

```rust
let x = {
    // This is a block expression, which means it will return a value
    let y = 5; // This is a statement
    y + 1 // This is an expression that evaluates to 6
}
// The value of `x` will be 6
```

> Rust is a  **expression-oriented** language, which means most constructs are expressions that evaluate to a value.

## 🏗️ Function Definition

```rust
fn function_name(parameter1: Type, parameter2: Type, ...) -> ReturnType {
    // Function body
    // ...
    return value;
    // or just
    value // without the return keyword and semicolon
}
```

- Functions in Rust are defined using the `fn` keyword.
- Function names should be descriptive and use **snake_case**.
- Functions will return the last **expression** in the function body if no return statement is provided.
- Function parameters and return types must be explicitly defined.
