# 🏘️ Vectors

## 👀 Fast Lookup

## ❓ What is a Vector?

A Vector is one of the **collection types** defined in the Rust standard library.

- It is a **growable array** that can store multiple values of the **same type**.
  - **Growable** means that the size of the vector can change dynamically at runtime.
  - **Same type** means that all elements in the vector must be of the same data type.
    - It uses **generics** internally to allow for different types of vectors.
- Vectors are implemented as a contiguous block of memory, similar to arrays.

## 🛠️ How to create a Vector?

To create a new vector in Rust, you can use the `Vec::new()` function or the `vec!` macro.

### Using `Vec::new()`

Compiler doesn't know the type of the vector, so you need to specify it explicitly.

```rust
let mut v: Vec<i32> = Vec::new();
```

### Using the `vec!` macro

In this case, the compiler can infer the type of the vector from the values you provide.

```rust
let v = vec![1, 2, 3];
```

## 📝 How to use a Vector?

### Creating and Modifying Vectors

```rust
// Creating vectors
let mut v_mutable = vec![1, 2, 3]; // Able to modify elements
let v_immutable = vec![4, 5, 6]; // Immutable, cannot modify elements

// Adding elements
v_mutable.push(4); // Adds 4 to the end of the vector
// v.immutable.push(7); // Error: cannot modify an immutable vector
```

### Accessing Elements

There are two ways to access elements in a vector:

- Get the reference to the element using the index
  - It will panic at runtime if the index is out of bounds.
- Using the `get` method
  - It returns an `Option<&T>`, which is `Some(&value)` if the index is valid, or `None` if the index is out of bounds.

```rust
// Accessing elements using index
let num_vec = vec![1, 2, 3];
let first_element = &num_vec[0]; // Accesses the first element
let second_element = &num_vec[1]; // Accesses the second element
// let error_element = &num_vec[3]; // This will panic at runtime if the index is out of bounds

// Accessing elements using the `get` method
let third_element = num_vec.get(2); // Returns an `Option<&i32>`
match third_element {
    Some(value) => println!("Third element: {}", value),
    None => println!("No third element found"),
}
```

#### Complicated Ownership and Borrowing in Vectors

When you have a mutable vector and you want to borrow an element from it, you need to be careful about the ownership and borrowing rules in Rust.

```rust
let mut v = vec![1, 2, 3];
let first_element = &v[0]; // Borrowing the first element
v.push(4); // Modifying the vector
// println!("First element: {}", first_element); // This will cause a compile-time error because the vector was modified after borrowing
```

#### Iterating Over Vectors

```rust
let v_immutable = vec![1, 2, 3, 4, 5];
for element in &v_immutable {
    println!("{}", element); // Prints each element in the vector
}

let mut v_mutable = vec![1, 2, 3, 4, 5];
for element in &mut v_mutable {
    *element += 1; // Modifies each element in the vector
}
```

## Using Enums in Vectors

We can leverage enum system to create a vector that can hold different types of values.

```rust
enum Value {
    Integer(i32),
    Float(f64),
    Text(String),
}

fn main() {
    let mut values: Vec<Value> = Vec::new();
    values.push(Value::Integer(42));
    values.push(Value::Float(3.14));
    values.push(Value::Text(String::from("Hello, world!")));

    for value in values {
        match value {
            Value::Integer(i) => println!("Integer: {}", i),
            Value::Float(f) => println!("Float: {}", f),
            Value::Text(s) => println!("Text: {}", s),
        }
    }
}