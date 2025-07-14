# 🍱 Structs and Methods

- [🍱 Structs and Methods](#-structs-and-methods)
  - [👀 Fast Lookup](#-fast-lookup)
  - [🏗️ Classic Structs CRUD(Create, Read, Update and Define)](#️-classic-structs-crudcreate-read-update-and-define)
  - [🔮 Non Classic Structs](#-non-classic-structs)
    - [🎯 Structs without Named Fields](#-structs-without-named-fields)
    - [👻 Structs without Fields](#-structs-without-fields)
  - [🍰 Methods](#-methods)

## 👀 Fast Lookup

- **Structs**: Custom data types
- **Methods**: Functions associated with structs

## 🏗️ Classic Structs CRUD(Create, Read, Update and Define)

Structs are custom data types that let you package together and name multiple related values that make up a meaningful group.

```rust
// Define: Define a struct
struct User {
        active: bool,
        username: String,
        email: String,
        sign_in_count: u64,
}

// Create: Create an instance
let user1 = User {
        active: true,
        username: String::from("someusername123"),
        email: String::from("someone@example.com"),
        sign_in_count: 1,
};

// Read: Access fields using dot notation
println!("Username: {}", user1.username);

// Create: Create another instance using update syntax
let user2 = User {
        email: String::from("another@example.com"),
        ..user1
};

// Create: Create with build function
fn build_user(email: String) -> User {
        User {
                active: true,
                username: String::from("someusername123"),
                email, // use the parameter directly
                sign_in_count: 1,
        }
}

let user3 = build_user(String::from("third@example.com"));

// Update: Update fields using dot notation
let mut user4 = User { ..user3 }; // Create a mutable instance from user3
user4.email = String::from("fourth@example.com");
```

## 🔮 Non Classic Structs

### 🎯 Structs without Named Fields

- **Tuple Structs**: These structs have unnamed fields and are useful for grouping related data without needing to name each field.

```rust
struct Color(i32, i32, i32); // Tuple struct with three i32 fields
struct Point(f64, f64, f64); // Tuple struct with three f64 fields

let black = Color(0, 0, 0); // Create an instance of Color
let origin = Point(0.0, 0.0, 0.0);
```

### 👻 Structs without Fields

- **Unit-Like Structs**: These structs have no fields and are useful for types that don't need to store data but still need a distinct type.

... I don't know why they exists, maybe I will realize why they exist later. // TODO: Add more notes

## 🍰 Methods

Methods are functions that are associated with a struct. They allow you to define behavior for your structs.

Following is an example of how to define and use methods in Rust: Focus on how methods handle ownership, borrowing, and mutability.

```rust
#[derive(Debug)] // Derive the Debug trait to enable printing the struct with {:?}
struct Rectangle {
    width: u32,
    height: u32,
}

impl Rectangle {
    // Takes an immutable reference to self
    fn get_area(&self) -> u32 {
        self.width * self.height
    }

    // Takes a mutable reference to self
    fn make_square(&mut self) {
        if self.width > self.height {
            self.height = self.width;
        } else {
            self.width = self.height;
        }
    }

    // Takes ownership of self and consumes it
    fn destroy(self) {
        println!(
            "Rectangle with width {} and height {} destroyed",
            self.width, self.height
        );
    }

    // Takes an immutable reference to self and another Rectangle
    fn can_hold(&self, other: &Rectangle) -> bool {
        self.width >= other.width && self.height >= other.height
    }

    // Associated(static) method to create a square. returns a new instance of Rectangle
    fn square(size: u32) -> Self {
        Self {
            width: size,
            height: size,
        }
    }
}

fn main() {
    let rect1 = Rectangle {
        width: 30,
        height: 50,
    };

    // Call the get_area method
    println!("Area of rect1: {}", rect1.get_area());

    // Call the make_square method
    let mut rect2 = Rectangle {
        width: 20,
        height: 40,
    };
    rect2.make_square();
    println!("rect2 after make_square: {:?}", rect2);

    // Call the can_hold method
    let rect3 = Rectangle {
        width: 10,
        height: 20,
    };
    println!("rect1 can hold rect3: {}", rect1.can_hold(&rect3));

    // Call the square associated method
    let square = Rectangle::square(15);
    println!("Square created with size 15: {:?}", square);

    // Call the destroy method
    rect1.destroy();
}
```
