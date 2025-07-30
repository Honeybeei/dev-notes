# Rust Programming Learning Plan

## 1. Plan Overview

- **Goal:** To finish reading 'The Rust Programming Language' and systematically learn Rust's core concepts to complete the final project (a multithreaded web server).
- **Learning Method:**
    1. **Preparation (YouTube):** Quickly watch YouTube lectures on the topic to get an outline of the concepts.
    2. **Main Study (The Book):** Carefully read 'The Rust Programming Language' and run the example code yourself.
    3. **Review (Note-taking):** Internalize the knowledge by summarizing what you've learned in your own words.
- **Total Estimated Duration:** Approx. 4 weeks (26 days)
- **Daily Study Time:** 3 to 5 hours

---

## 2. Daily Learning Plan

### Week 1: Mastering the Basics & Core Concepts

---
<!-- 
**Day 1 (approx. 3.5 hours)**

- 1.1. Installation
- 1.2. Hello, World!
- 1.3. Hello, Cargo
- 2. Programming a Guessing Game -->
<!-- 
**Day 2 (approx. 4.2 hours)**

- 3.1. Variables and Mutability
- 3.2. Data Types
- 3.3. Functions
- 3.4. Comments
- 3.5. Control Flow -->
<!-- 
**Day 3 (approx. 5 hours) 👑**

- 4.1. What is Ownership?
- 4.2. References and Borrowing
- *Today you will learn the most important concept in Rust. Invest enough time.* -->
<!-- 
**Day 4 (approx. 3 hours)**

- 4.3. The Slice Type
- 5.1. Defining and Instantiating Structs

**Day 5 (approx. 3.5 hours)**

- 5.2. An Example Program Using Structs
- 5.3. Method Syntax
- 6.1. Defining an Enum
 -->
<!-- **Day 6 (approx. 3.5 hours)**

- 6.2. The `match` Control Flow Construct
- 6.3. Concise Control Flow with `if let`
- 7.1. Packages and Crates
- 7.2. Defining Modules to Control Scope and Privacy

**Day 7 (approx. 3 hours)**

- 7.3. Paths for Referring to an Item in the Module Tree
- 7.4. Bringing Paths into Scope with the `use` Keyword
- 7.5. Separating Modules into Different Files
- 8.1. Storing Lists of Values with Vectors -->

### Week 2: Practical Tools & The Second Hurdle

---

**Day 8 (approx. 3.5 hours)**

<!-- - 8.2. Storing UTF-8 Encoded Text with Strings -->
- 8.3. Storing Keys with Associated Values in Hash Maps
- 9.1. Unrecoverable Errors with `panic!`

**Day 9 (approx. 3.2 hours)**

- 9.2. Recoverable Errors with `Result`
- 9.3. To `panic!` or Not to `panic!`

**Day 10 (approx. 5 hours) 👑**

- 10.1. Generic Data Types
- 10.2. Traits: Defining Shared Behavior
- *Today you will learn the core of abstraction: generics and traits. It's difficult but very important.*

**Day 11 (approx. 3-4 hours) 👑**

- 10.3. Validating References with Lifetimes
- *Today is dedicated solely to lifetimes. Think of it as learning to talk to the compiler.*

**Day 12 (approx. 3.7 hours)**

- 11.1. How to Write Tests
- 11.2. Controlling How Tests Are Run
- 11.3. Test Organization
- 12.1. Accepting Command Line Arguments
- 12.2. Reading a File

**Day 13 (approx. 3 hours)**

- 12.3. Refactoring to Improve Modularity and Error Handling
- 12.4. Developing a Library’s Functionality with Test-Driven Development

**Day 14 (approx. 3 hours)**

- 12.5. Working with Environment Variables
- 12.6. Writing Error Messages to Standard Error Instead of Standard Output
- 13.1. Closures

### Week 3: Deep Dive & Advanced Features

---

**Day 15 (approx. 3.5 hours)**

- 13.2. Processing a Series of Items with Iterators
- 13.3. Improving Our I/O Project
- 13.4. Comparing Performance: Loops vs. Iterators

**Day 16 (approx. 3.5 hours)**

- Chapter 14. More About Cargo and Crates.io (All)
- 15.1. `Box<T>` for Pointing to Data on the Heap
- 15.2. Treating Smart Pointers Like Regular References with the `Deref` Trait

**Day 17 (approx. 3.5 hours)**

- 15.3. Running Code on Cleanup with the `Drop` Trait
- 15.4. `Rc<T>`, the Reference Counted Smart Pointer
- 15.6. Reference Cycles Can Leak Memory

**Day 18 (approx. 3.5 hours)**

- 15.5. `RefCell<T>` and the Interior Mutability Pattern
- 16.1. Using Threads to Run Code Simultaneously

**Day 19 (approx. 3.5 hours)**

- 16.2. Using Message Passing to Transfer Data Between Threads
- 16.3. Shared-State Concurrency

**Day 20 (approx. 3.7 hours)**

- 16.4. Extensible Concurrency with the `Sync` and `Send` Traits
- 17.1. Characteristics of Object-Oriented Languages
- 17.2. Using Trait Objects That Allow for Values of Different Types
- 17.3. Implementing an Object-Oriented Design Pattern

**Day 21 (approx. 4.2 hours)**

- 18.1. All the Places Patterns Can Be Used
- 18.2. Refutability: Whether a Pattern Might Fail to Match
- 18.3. Pattern Syntax

### Week 4: Final Project & Wrap-up

---

**Day 22 (approx. 4 hours)**

- 19.1. Unsafe Rust
- 19.2. Advanced Traits

**Day 23 (approx. 3.5 hours+)**

- 19.3. Advanced Types
- 19.4. Advanced Functions and Closures
- 19.5. Macros
- *Chapter 19 is very deep and may be difficult to digest in one day. It's okay to take two days.*

**Day 24 (approx. 4-5 hours) 🏆**

- 20.1. Building a Single-Threaded Web Server
- *Finally, the final project begins!*

**Day 25 (approx. 5 hours+) 🏆**

- 20.2. Turning Our Single-Threaded Server into a Multithreaded Server
- *If it's hard to finish in one day, split it into two. This is the most crucial part.*

**Day 26 (approx. 3 hours or more)**

- 20.3. Graceful Shutdown and Cleanup
- **Total Review & Code Refactoring**
- *Look back at all the code you've written and find areas for improvement.*
