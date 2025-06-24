# 📮 Variables

- [📮 Variables](#-variables)
  - [👀 Fast Lookup](#-fast-lookup)
  - [♻️ Mutability](#️-mutability)
  - [🔒 Constants](#-constants)
  - [👥 Shadowing](#-shadowing)
    - [👻 Scope of Shadowing](#-scope-of-shadowing)

## 👀 Fast Lookup

- **Variables**: Immutable by default, use `mut` for mutability
- **Constants**: `const NAME: type = value;` - compile-time evaluated
- **Shadowing**: `let x = new_value;` - reuse variable names, can change types

## ♻️ Mutability

- Variables in Rust are **immutable** by default.
- Make a variable mutable by using the `mut` keyword.

## 🔒 Constants

> ❓ Why Constants exists even though there are immutable variables?

- Constants are calculated at compile time, while immutable variables are calculated at runtime.
- Constants are always immutable and must be explicitly declared with the `const` keyword.

```rust
const THREE_HOURS_IN_SECONDS: u64 = 60 * 60 * 3;
```

## 👥 Shadowing

- Rust allows you to **shadow** a variable by declaring a new variable with the same name.
- This is useful for changing the type of a variable or modifying its value without using `mut`.

```rust
let x = 5;
// x =  x + 1; // Error: cannot assign twice to immutable variable `x`
let x = x + 1; // x is now 6. Shadowing needs `let` keyword.
let x = "Hello"; // x is now a string -> Changed type from integer to string
```

### 👻 Scope of Shadowing

- Shadowing is limited to the scope in which it is defined.

```rust
let x = 5;
{
    let x = x + 1; // This shadows the outer `x`
    println!("Inner x: {}", x); // Prints 6
}
println!("Outer x: {}", x); // Prints 5
```
