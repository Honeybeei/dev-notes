# 🔢 Enums

- [🔢 Enums](#-enums)
  - [👀 Fast Lookup](#-fast-lookup)
  - [❓ What is an Enum?](#-what-is-an-enum)
  - [📐 The `Shape` Enum Example](#-the-shape-enum-example)
  - [🤔 Option Enum](#-option-enum)
  - [🔀 `match` and `if let`](#-match-and-if-let)

## 👀 Fast Lookup

- **Enum**: A type that can be one of several different variants.
- **Variants**: Different types or forms that an enum can take.
- `match` and `if let`: Control flow constructs to handle enum variants.
- **Option Enum**: A special enum that represents a value that can be either `Some(value)` or `None`, used to handle optional values safely.

## ❓ What is an Enum?

Enum in Rust is a **Group of related types(variants)** like a *union type in Typescript*. It is a way to define a type that can be one of several different variants. Each variant can have its own data and behavior.

- `struct` is a **data structure** that can hold this **and** that type.
- `enum` is a **type** that can be this **or** that type.

## 📐 The `Shape` Enum Example

```rust
// Circle is a type that can hold a number and a tuple
struct Circle {
    radius: f64,
    center: (f64, f64),
}

// Rectangle is a type that can hold two numbers and a tuple
struct Rectangle {
    width: f64,
    height: f64,
    top_left: (f64, f64),
}

// Shape can be either a line, circle, or rectangle
enum Shape {
    Line { start: (f64, f64), end: (f64, f64) }, // A line defined by a field of start and end points
    Circle(Circle),                              // A circle defined by a `Circle` struct
    Rectangle(Rectangle),                        // A rectangle defined by a `Rectangle` struct
}

// We can implement methods on the `Shape` enum like we do with structs
impl Shape {
    // Method to calculate the area of the shape
    fn area(&self) -> f64 {
        match self { // This is a match expression (switch in other languages)
            // Condition => {Action}
            Shape::Line { .. } => 0.0, // Lines have no area
            Shape::Circle(circle) => std::f64::consts::PI * circle.radius.powi(2), // Area of a circle
            Shape::Rectangle(rectangle) => rectangle.width * rectangle.height, // Area of a rectangle
            // There will be a compile-time error if we forget to handle all variants
        }
    }
}
```

## 🤔 Option Enum

The `Option` enum in Rust is a way to represent a value that can either be something (`Some`) or nothing (`None`). It is like `?` in TypeScript. In Rust, it is defined as:

```rust
enum Option<T> {
    Some(T), // Contains a value of type T
    None,    // Represents the absence of a value
}
```

This means `Option<T>` can either be `Some(value)` or `None`. It is used to handle cases where a value might be absent, avoiding the need for **null** values.

> Why this structure is useful?
>
> In next section, we will see how to handle variants of an enum using `match` and `if let`, which restricts the code to handle all possible cases, making it safer and more predictable.

## 🔀 `match` and `if let`

It is similar to a `switch` statement in other languages, but more powerful.

- `match` is used to match against **all possible variants** of an enum.

```rust
match value {
    pattern1 => { /* action for pattern1 */ },
    pattern2 => { /* action for pattern2 */ },
    _ => { /* action for any other pattern */ }, // The wildcard pattern `_` matches
}
```

- `if let` is used to match against a single variant of an enum. (syntactic sugar for `match`)

```rust
if let pattern = value {
    // action for pattern
} else {
    // action for any other pattern
}
```
