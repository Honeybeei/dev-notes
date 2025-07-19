# 🎁 Packages, Creates and Modules

- [🎁 Packages, Creates and Modules](#-packages-creates-and-modules)
  - [👀 Fast Lookup](#-fast-lookup)
  - [🏗️ Packages and Crates](#️-packages-and-crates)
    - [🧐 Huh?? moment](#-huh-moment)
  - [🧩 Modules](#-modules)
    - [🤔 Why do we need modules?](#-why-do-we-need-modules)
    - [🛠️ How to create modules?](#️-how-to-create-modules)
    - [🚀 How to use modules?](#-how-to-use-modules)

## 👀 Fast Lookup

## 🏗️ Packages and Crates

- **Package** is a collection of one or more crates
- **Crate** is a group of Rust source files that can be compiled into a library or executable
  - **Binary Crate**: An executable program. Must have a `main` function.
  - **Library Crate**: A reusable library that can be used by other crates.
- **Module(`mod`)** is a way to organize code within a crate, allowing for better structure and visibility control.
- **Crate Root**: The main file of a crate, which is either `src/main.rs` for binary crates or `src/lib.rs` for library crates.
- `Cargo.toml` is the manifest file for Rust projects, containing metadata about the package, dependencies, and build configuration.

> A package can have:
>
> - One or more crates
>   - Can have more than one binary crate
>   - Can not have more than one library crate
> - A `Cargo.toml` file

### 🧐 Huh?? moment

> It was hard for me to understand why a package can have multiple binary crates but only one library crate.
> 🤓 The conclusion I came to is that package is not just a single executable program but a collection of related crates that can be built or shared.
>
> - Library crate contains core logic and shared functionality. And package is an API that can be used by other packages. Therefore, a package should have only one library crate.
> - A single package can have multiple binary crates to provide different entry points or applications that use the shared library crate.

Let's say we are creating "Awesome Video Editor" package.

- **Library Crate** (`src/lib.rs`):
  - Contains core functionality like video processing, filters, and effects.
  - Can be used by other packages or applications.
- **Binary Crates**
  - `src/main.rs`: The main entry point for the application.
  - `src/bin/converter.rs`: A simple video format converter.
  - `src/bin/uploader.rs`: A tool to upload videos to a cloud service.

Like this, the package can have multiple binary crates that provide different functionalities, but only one library crate that contains the core logic and shared functionality.

## 🧩 Modules

### 🤔 Why do we need modules?

Modules in Rust are used to:

- To **organize code** into separate namespaces, making it easier to manage and understand.
- To **control the visibility** of items (functions, structs, etc.) and prevent naming conflicts.

### 🛠️ How to create modules?

- To create a module in Rust, you use the `mod` keyword.
- Elements such as functions, structs, and enums can expose items from a module using the `pub` keyword, which makes them public and accessible from outside the module.

```rust
// src/lib.rs
mod video {
    pub fn process_video() {
        // Video processing logic
    }

    pub fn upload_video() {
        // Video uploading logic
    }

    fn private_helper() {
        // This function is private to the module
    }
}
```

### 🚀 How to use modules?

To use modules in Rust, you need to bring the elements into scope. To do this, we have to specify the **path** of the elements we want to use.

- **Absolute Path**: The full path from the crate root (e.g., `crate::video::process_video`).
  - `crate` refers to the root of the current crate. (`main.rs` or `lib.rs`)
- **Relative Path**: The path relative to the current module (e.g., `self::process_video`).

- To use a module, you can:
  - Directly refer to it using the `mod_name::item_name` syntax.
  - Alternatively, you can use the `use` keyword to bring items into scope.

Let's say we have a module named `video` with a function `upload_video` that we want to use in our main application.

This is the file structure:

```plaintext
src/
├── main.rs
└── video.rs
```

We can create a module in `video.rs`:

> By the way, you can create a module by using `mod` keyword or by creating a separate file with the same name as the module.
>
> This was bit confusing. But the way I understood it is that:
> using `mod` keyword is more like declaring a module inline, while creating a separate file is like defining the module in its own file.

```rust
// src/video.rs
pub fn process_video() {
    // Video processing logic
}

pub fn upload_video() {
    // Video uploading logic
}

fn private_helper() {
    // This function is private to the module
}
```

Now, we can use this module in our `main.rs` file:

```rust
// src/main.rs
mod video;

use crate::video::upload_video;

fn main() {
    // Directly refer to the module
    crate::video::process_video();

    // using `use` to bring the function into scope
    upload_video();
}
```

This allows you to call the `process_video` function from the `video` module in your main application.
