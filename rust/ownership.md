# 🔒 Ownership

- [🔒 Ownership](#-ownership)
  - [👀 Fast Lookup](#-fast-lookup)
  - [📋 Ownership Rules](#-ownership-rules)
  - [🏗️ Heap vs Stack Data](#️-heap-vs-stack-data)
  - [🔗 References and Borrowing](#-references-and-borrowing)
    - [📜 Rules of References](#-rules-of-references)
  - [🍰 Slices](#-slices)
    - [🔤 String Slices](#-string-slices)
    - [🔢 Other Slices](#-other-slices)

## 👀 Fast Lookup

- **Ownership**: Every value has a single, unique owner. When the owner goes out of scope, the value is automatically dropped (deallocated). This prevents memory leaks.
- **Move**: When you assign a heap-allocated value to another variable, ownership is *moved*. The original variable becomes invalid. This prevents double-free errors.
- **Borrowing**: You can *borrow* access to a value by using a reference (`&`). The owner retains ownership.
- **Mutability Rules**: You can have either:
  - One mutable reference (`&mut`) **OR**
  - Any number of immutable references (`&`).
    - This rule prevents data races at compile time.
- **Slices**: A slice is an immutable reference to a contiguous sequence of elements in a collection.

## 📋 Ownership Rules

Ownership is Rust's mechanism for managing memory. Its primary goal is to ensure the safe handling of data stored on the **heap**, like a `String` or a `Vec<T>`.

> ✅ **The Three Ownership Rules**
>
> 1. Each value in Rust has a variable that's called its **owner**.
> 2. There can only be **one owner** at a time.
> 3. When the owner goes out of scope, the value will be **dropped**.

## 🏗️ Heap vs Stack Data

Why does this matter for the heap? Because heap data doesn't clean itself up automatically. Ownership ensures that for every piece of data on the heap, there's exactly one owner responsible for cleaning it up when it's no longer needed.

- **Heap-Allocated Data (e.g., `String`)**: These values follow the full ownership rules. When you reassign them, ownership is moved.

```rust
fn main() {
    // s1 owns the String data allocated on the heap.
    let s1 = String::from("hello");

    // Ownership of the String data is moved from s1 to s2.
    // s1 is no longer valid and cannot be used.
    let s2 = s1;

    // println!("s1 is: {}", s1); // Compile-time error: value borrowed here after move
    println!("s2 is: {}", s2); // This is valid.

} // s2 goes out of scope, and the String data is dropped (freed).
```

- **Stack-Allocated Data (e.g., `i32`, `bool`)**: These types have a known, fixed size and implement the `Copy` trait. Instead of moving, a bit-for-bit copy is made. Both the original and the copy are valid.

```rust
fn main() {
    // x is an integer stored on the stack.
    let x = 5;

    // A copy of x's value is made and bound to y.
    // Both x and y are independent and valid.
    let y = x;

    println!("x = {}, y = {}", x, y); // Perfectly valid!
}
```

> My personal take
>
> - For me, **Ownership** looks like giving restrictions for handling pointers and references at compile time, which is a good thing.
> - This was quite confusing for me at first, but I realized that it would be impossible to use the same value in multiple places if ownership was applied to stack-allocated values as well. This would lead to unnecessary restrictions and complexity in the code.

## 🔗 References and Borrowing

What if you want to use a value without taking ownership? You can borrow it by creating a reference. A reference (&) is like a pointer that is guaranteed to be valid.

### 📜 Rules of References

1. At any given time, you can have either one mutable reference or any number of immutable references.
2. References must always be valid.

> Q: Why can we have multiple immutable references but only one mutable reference?
> A: This is to prevent data races at compile time. If multiple parts of the code could modify the same value simultaneously, it could lead to unpredictable behavior and bugs that are hard to track down.

```rust
fn calculate_length(s: &String) -> usize {
    s.len()
}

fn append_to_string(s: &mut String) {
    s.push_str(", world!"); // Modifying through a mutable reference
}

fn main() {
    let s1 = String::from("Hello");
    let len = calculate_length(&s1); // Passing an immutable reference
    println!("The length of '{}' is {}.", s1, len); // s1 is still valid

    let mut s2 = String::from("Hello");
    append_to_string(&mut s2); // Passing a mutable reference
    println!("{}", s2); // s2 is now "Hello, world!"
}
```

## 🍰 Slices

A **slice** is a reference to a contiguous sequence of elements in a collection rather than the whole collection. It allows you to work with a portion of data without taking ownership.

Slices are a type of reference so they follow the same borrowing rules.

### 🔤 String Slices

A string slice (`&str`) is a reference to part of a `String`.

```rust
fn first_word(s: &String) -> &str {
    let bytes = s.as_bytes();

    for (i, &item) in bytes.iter().enumerate() {
        if item == b' ' {
            return &s[0..i]; // Return a slice of the string
        }
    }

    &s[..] // Return a slice(immutable reference) of the whole string
}

fn main() {
    let my_string = String::from("hello world");

    // `word` is a reference to a part of `my_string`
    let word = first_word(&my_string);

    // my_string.clear(); // Error! Cannot take a mutable reference
                         // because an immutable one (the slice) exists.

    println!("The first word is: {}", word);

    // The slice `word` goes out of scope here, so we can now mutate `my_string` again.
}
```

### 🔢 Other Slices

The same slicing syntax can be used on arrays and other collections.

```rust
fn main() {
    let a = [1, 2, 3, 4, 5];

    // Create a slice containing elements from index 1 to 3 ([2, 3, 4])
    let slice = &a[1..4];

    assert_eq!(slice, &[2, 3, 4]);
    println!("The slice is: {:?}", slice);
}
```
