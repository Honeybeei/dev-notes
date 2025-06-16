# 👋 Hello World

- [👋 Hello World](#-hello-world)
  - [👀 Fast Lookup](#-fast-lookup)
  - [⚙️ Initial Setup and Keywords](#️-initial-setup-and-keywords)
  - [💻 Hello World Example](#-hello-world-example)
  - [🔍 Example deep dive](#-example-deep-dive)

## 👀 Fast Lookup

This note is a simple "Hello World" example in Rust.

## ⚙️ Initial Setup and Keywords

Install Rust using `rustup`, which is the recommended way to install Rust. It manages Rust versions and associated tools.

- `rustup` commands:
  - `rustup update`: Updates Rust to the latest version.
  - `rustup doc`: Opens the Rust documentation in the browser.

## 💻 Hello World Example

**main.rs:**

```rust
fn main() {
    println!("Hello, world!");
}
```

To run the program, use the following commands in your terminal:

```bash
rustc main.rs  # Compiles the Rust code
./main        # Runs the compiled Rust program
```

This will output:

```plaintext
Hello, world!
```

## 🔍 Example deep dive

- The `main` function is the entry point of a Rust program.
- Rust uses 4 spaces for indentation.
- `println!` is a macro that prints text to the console. The `!` indicates that it is a macro, not a function.
  - In this stage, let's just understand that macros and functions are a bit different.
- `;` is used to denote the end of a statement in Rust.
- `rustc` is the Rust compiler that compiles the source code into an executable binary.
  - We will use `cargo` for managing projects and dependencies later, which simplifies this process instead of using `rustc` directly.
