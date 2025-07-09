# 📝 Stack and Heap

Both the **stack** and **heap** are memory areas where data is stored during program execution. However, they have different structures and are used for different purposes.

- [📝 Stack and Heap](#-stack-and-heap)
  - [👀 Fast Lookup](#-fast-lookup)
  - [📚 Stack](#-stack)
    - [⚙️ How Stack Works](#️-how-stack-works)
    - [✨ Stack Characteristics](#-stack-characteristics)
  - [🏔️ Heap](#️-heap)
    - [⚙️ How Heap Works](#️-how-heap-works)
    - [✨ Heap Characteristics](#-heap-characteristics)
  - [🔍 Example: Stack and Heap in Action](#-example-stack-and-heap-in-action)
    - [📝 Step-by-Step Memory Flow](#-step-by-step-memory-flow)
  - [🤔 Why This Distinction Matters](#-why-this-distinction-matters)

## 👀 Fast Lookup

**Stack**: FILO structure, fast access, auto cleanup, fixed-size data
**Heap**: Random access, slower, dynamic allocation, variable-size data  
**Function Frame**: Stack block containing locals, params, return address
**Pointer**: Stack variable holding heap address for dynamic data

## 📚 Stack

The stack is a **First-In, Last-Out (FILO)** data structure that stores data with a fixed size known at compile time.

### ⚙️ How Stack Works

**When a function is called:**

1. A **function frame** is created and pushed onto the stack
    - The function frame is a block of fixed-size memory allocated for the function call
    - It contains local variables, function parameters, and return address
    - The system knows exactly how much memory to allocate because all data has a known size at compile time

2. **When the function returns:**
    - The frame is popped off the stack
    - All data in that frame is automatically cleaned up
    - Memory is instantly available for reuse

### ✨ Stack Characteristics

- **Very fast access** - data is always at the top of the stack
- **Automatic memory management** - cleanup happens when functions return
- **Limited size** - typically a few megabytes
- **Fixed-size data only** - integers, floats, arrays with known sizes

## 🏔️ Heap

The heap is a **random access memory area** used for data whose size is not known at compile time or can change during runtime.

### ⚙️ How Heap Works

**Memory allocation:**

- Programs request memory from the heap dynamically
- The system finds available space and returns a memory address
- This address is stored in a pointer variable (usually on the stack)

**Memory access:**

- Access requires following the pointer to the heap location
- Slower than stack access due to indirection
- Can access any part of allocated memory randomly

### ✨ Heap Characteristics

- **Dynamic size** - can grow and shrink during runtime
- **Manual or automatic management** - depends on the language
- **Larger capacity** - limited by available system memory
- **Slower access** - requires pointer dereferencing

## 🔍 Example: Stack and Heap in Action

```rust
fn main() {
     let age = 30; // Stored on the stack
     let name = String::from("Jun"); // Stored on the heap
     println!("Name: {}, Age: {}", name, age);
}
```

### 📝 Step-by-Step Memory Flow

**1. Function Call (`main` is called)**

- A stack frame is created and pushed onto the stack
- The system needs to know how much memory to allocate for this function

**2. Variable Allocation**

- `age = 30`: This is a fixed-size integer (4 bytes)
  - Stored directly on the stack within the function frame
  - System knows exact memory requirement at compile time

- `name = String::from("Jun")`: This is a complex, dynamic type
  - System doesn't know the final size at compile time (strings can grow)
  - **Stack portion**: A pointer (8 bytes) is allocated on the stack to store the heap address
  - **Heap portion**: The actual string data "Jun" is allocated on the heap
  - The stack pointer points to the heap location containing the string data

**3. Memory Layout**

```plaintext
Stack Frame:              Heap:
┌─────────────────────┐   ┌─────────────┐
│ age: 30             │   │ "Jun"       │ ← actual string data
│ name: [pointer] ────────→             │
│ return address      │   └─────────────┘
└─────────────────────┘
```

**4. Function Return**

- The stack frame is popped off the stack
- **Stack cleanup**: `age` and the `name` pointer are automatically removed
- **Heap cleanup**: The String data on the heap is deallocated (in Rust, this happens automatically through the ownership system)
- Both stack and heap memory are now freed and available for reuse

## 🤔 Why This Distinction Matters

**Stack is ideal for:**

- Local variables with known sizes
- Function parameters
- Fast, temporary data

**Heap is necessary for:**

- Dynamic data structures (strings, vectors, trees)
- Data that outlives the function that created it
- Large data that would overflow the stack
