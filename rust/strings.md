# 🧵 Strings

- [🧵 Strings](#-strings)
  - [👀 Fast Lookup](#-fast-lookup)
  - [🏷️ Types of Strings in Rust](#️-types-of-strings-in-rust)
  - [🤔 When to use `&str` vs `String`](#-when-to-use-str-vs-string)
  - [🔧 Working with Strings](#-working-with-strings)

## 👀 Fast Lookup

- `&str`: Hardcoded string literal, immutable, and not heap-allocated.
- `String`: Heap-allocated, mutable, and can grow in size.
- Use `&str` for static strings and `String` for dynamic strings.
- Use `chars()` for most character operations, but be aware of performance implications.

## 🏷️ Types of Strings in Rust

- `&str`: Core string type, borrowed, immutable, and not heap-allocated.
- `String`: Owned string type, defined in the standard library, mutable, heap-allocated, and can grow in size. It is a wrapper around a `Vec<u8>` that guarantees valid UTF-8.
- ...

## 🤔 When to use `&str` vs `String`

- Use `&str` when you
  - You're writing a function that only needs to read a string, not change it. This is more flexible because you can pass both a String and a &str to it!
  - You want to pass a string literal.
- Use `String` when you
  - Need to create or modify string data at runtime.
  - Need a function to return a string that it creates.
  - Need to store a string in a struct that should own its data.

## 🔧 Working with Strings

Rust's `String` and `&str` types are UTF-8 encoded, which means a single character can take up to 4 bytes. This means calling `len()` will not guarantee the number of characters. Also, indexing into a `String` or `&str` with a number will panic if the index is not valid. Then how do you get the number of characters in a string and access characters safely?

- Use the `chars()` method to iterate over characters in a string.
  - `chars().count()` returns the number of characters in a string.
  - Use `for c in text.chars()` to iterate over characters.
  - `chars().nth(n)` returns the `Option<char>` at index `n`, which is safe.

However, `chars()` is not fast. It has O(n) complexity because it has to iterate through the string to count characters.

My conclusion is that use `chars()` as default for character related operations. However, if we are dealing with a lot of characters and performance is critical, use slicing `&str[start..end]` to get a substring, which is O(1) because it just creates a new `&str` that points to the same data without copying.
