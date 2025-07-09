# 📊 Data Types

- [📊 Data Types](#-data-types)
  - [👀 Fast Lookup](#-fast-lookup)
  - [🔍 Overview of Rust Data Types](#-overview-of-rust-data-types)
  - [🔢 Scalar Types](#-scalar-types)
    - [🔢 Integer Type](#-integer-type)
    - [🔢 Floating-Point Type](#-floating-point-type)
    - [✅ Boolean Type](#-boolean-type)
    - [🔤 Character Type](#-character-type)
  - [📦 Compound Types](#-compound-types)
    - [📊 Tuple Type](#-tuple-type)
    - [📋 Array Type](#-array-type)

## 👀 Fast Lookup

- **Scalar Types**: Single value types like
  - **integers**: `i8`, `u8`, ... `isize`, `usize`
  - **floating-point numbers**: `f32`, `f64`
  - **booleans**: `true`, `false`
  - **characters**: `'a'`, `'😊'`
- **Compound Types**: Types that can group multiple values
  - **tuples**: Fixed size collection of **different types**.
  - **arrays**: Fixed size collection of the **same type**.

## 🔍 Overview of Rust Data Types

- Rust is a **statically typed** language, meaning all variables must have a type at compile time.
- Rust has two main categories of data types: **scalar** and **compound**.

## 🔢 Scalar Types

- Scalar types represent a single value.
- They include:
  - **Integer Type**: Numbers without a fractional component.
  - **Floating-Point Type**: Numbers with a fractional component.
  - **Boolean Type**: Represents a value that can be either `true` or `false`.
  - **Character Type**: Represents a single Unicode character.

### 🔢 Integer Type

- Signed and unsigned integers of various sizes.
  - 8-bit: `i8`, `u8`
  - 16-bit: `i16`, `u16`
  - 32-bit: `i32`, `u32`
  - 64-bit: `i64`, `u64`
  - 128-bit: `i128`, `u128`
  - Arch-specific: `isize`, `usize`
    -  `isize` is signed, `usize` is unsigned and depends on the architecture (32-bit or 64-bit).

> How Rust handles integer overflow:
>
> - In debug mode, Rust will **panic** on overflow.
> - In release mode, it will **wrap around**.
> I will create a separate section for this topic.

### 🔢 Floating-Point Type

- Represents numbers with a fractional component.
- Two types:
  - `f32`: 32-bit floating-point number.
  - `f64`: 64-bit floating-point number (default type: More precise but almost same speed as `f32`).

### ✅ Boolean Type

- 1 bit size data type (**true** or **false**).

### 🔤 Character Type

- Represents a single Unicode character(4 bytes).
  - Which means it covers a wider range of characters than ASCII.
- `'` is used to represent characters in Rust.

```rust
let c: char = 'a'; // Example of a character type
let emoji: char = '😊'; // Example of a Unicode character
```

## 📦 Compound Types

### 📊 Tuple Type

- A fixed-size collection of values of different types.
- Defined using parentheses `()`.

```rust
let sample_tuple: (i32, f64, char) = (42, 3.14, 'x'); // we can have different types in a tuple

// Accessing tuple elements
let first_element = sample_tuple.0; // Accessing the first element
let second_element = sample_tuple.1; // Accessing the second element
let third_element = sample_tuple.2; // Accessing the third element
// let fourth_element = sample_tuple.3; // This will cause a compile-time error since the tuple has only three elements
let (x, y, z) = sample_tuple; // Destructuring a tuple
println!("x: {}, y: {}, z: {}", x, y, z); // Accessing destructured values
```

### 📋 Array Type

- A fixed-size collection of values of the same type.
  - Use **array** when you know the size of the collection at compile time.
  - Use **vector** when the size can change at runtime.
- Defined using square brackets `[]`.

```rust
// Defining arrays
let a: [i32; 3] = [1, 2, 3]; // Example of an array with three elements
let b = [3; 5]; // Example of an array with five elements, all initialized to 3

// Accessing array elements
let first_element = a[0]; // Accessing the first element


let user_input: i32 = ...; // Assume we get 10 from user input
error_element = a[user_input]; // Accessing out bound element
println!("{}", error_element); // This will cause a runtime panic
```

