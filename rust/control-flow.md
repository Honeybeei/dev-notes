# 🔁 Control Flow

- [🔁 Control Flow](#-control-flow)
  - [👀 Fast Lookup](#-fast-lookup)
  - [🤔 `if`, `else if`, `else`](#-if-else-if-else)
  - [🔄 `loop`, `while`, `for`](#-loop-while-for)

## 👀 Fast Lookup

- `condition` should be a boolean
- `if`, `else if`, and `else` are expressions
- `loop`, `while`, and `for` are used for iteration
- `break` to exit loops, `continue` to skip iterations

## 🤔 `if`, `else if`, `else`

```rust
if condition {
    // Code to execute if condition is true
} else if another_condition {
    // Code to execute if another_condition is true
} else {
    // Code to execute if all conditions are false
}
```

- `condition` should be a boolean expression.

```rust
let x = 5;

if x > 0 {
    println!("x is positive");
} else if x < 0 {
    println!("x is negative");
} else {
    println!("x is zero");`
}

// Error case: `condition` must be a boolean expression
if x {
    ... // This will cause a compile-time error because `x` is not a boolean
}
```

- `if`, `else if`, and `else` is an expression, meaning it returns a value.

```rust
fn main() {
    let condition = true;
    let number = if condition { 5 } else { 6 };

    println!("The value of number is: {number}");
}
```

## 🔄 `loop`, `while`, `for`

```rust
// Infinite loop
loop {
    // Code to execute repeatedly
    // Use `break` to exit the loop
}

// Loop with a condition
while condition {
    // Code to execute while condition is true
}

// Looping through a collection or range
for item in collection {
    // Code to execute for each item in the collection
}
```

- `break` is used to exit a loop.
- `continue` is used to skip the current iteration and continue with the next one.
