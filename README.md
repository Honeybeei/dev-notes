# 📝 Dev Notes

- [📝 Dev Notes](#-dev-notes)
  - [🧐 What is this repository about?](#-what-is-this-repository-about)
  - [📝 Notes](#-notes)
    - [💻 CS Knowledge](#-cs-knowledge)
    - [🗣️ Languages](#️-languages)
      - [❤️‍🩹 JavaScript, TypeScript](#️-javascript-typescript)
      - [🐍 Python](#-python)
      - [🐹 Go](#-go)
      - [🦀 Rust](#-rust)
    - [🤖 AI \& Machine Learning](#-ai--machine-learning)
    - [🎨 Design](#-design)
  - [📝 Note Guidelines](#-note-guidelines)

## 🧐 What is this repository about?

This repository is a collection of my **personal notes** and **cheat-sheets** for various programming languages, frameworks, and tools that I use in my development work. I often find it difficult to recall important details, particularly when switching between various programming languages and frameworks. This repository aims to provide a quick reference for myself and maybe others who might find it useful.

## 📝 Notes

### 💻 CS Knowledge

- [🧵 Character Encodings](./cs/character-encodings.md)

### 🗣️ Languages

#### ❤️‍🩹 JavaScript, TypeScript

- [🐣 Object Oriented Programming Template](./js-ts/oop-template.md)
- [🔁 Export and Import](./js-ts/export-import.md)

#### 🐍 Python

- [🗿 Constants](./python/constants.md)
- [📖 Docstrings](./python/docstrings.md)
- [🔧 Function Arguments](./python/function-arguments.md)
- [🔄 Generators](./python/generators.md)
- [🔁 Iterables and Iterators](./python/iterables-and-iterators.md)
- [⚡ Lambda Functions](./python/lambda-functions.md)
- [📦 Modules & Packages](./python/modules-packages.md)
- [😉 Type Hints](./python/type-hints.md)
- [📝 User Input/Output](./python/user-input-output.md)
- [⚡ UV](./python/uv.md)
- [🔒 With Context Manager](./python/with-context-manager.md)

#### 🐹 Go

- [📊 Arrays](./go/arrays.md)
- [🗿 Constants and Enums](./go/constants-and-enums.md)
- [🔀 Control Flow](./go/control-flow.md)
- [🔌 Interfaces](./go/interfaces.md)
- [⚙️ Methods](./go/methods.md)
- [📦 Packages and Modules](./go/packages-and-modules.md)
- [👉 Pointers](./go/pointers.md)
- [🔤 Strings](./go/strings.md)
- [🏗️ Structs](./go/structs.md)
- [📝 Variables](./go/variables.md)

#### 🦀 Rust

- [📖 Learning Materials](./rust/learning-material.md)
- [👋 Hello World](./rust/hello-world.md)
- [📦 Cargo](./rust/cargo.md)
- [📮 Variables](./rust/variables.md)
- [📊 Data Types](./rust/data-types.md)
- [🔧 Functions](./rust/functions.md)
- [🔁 Control Flow](./rust/control-flow.md)
- [📝 Stack and Heap](./rust/stack-and-heap.md)
- [🔒 Ownership](./rust/ownership.md)
- [🍱 Structs and Methods](./rust/structs-methods.md)
- [🔢 Enums](./rust/enums.md)
- [🎁 Packages, Creates and Modules](./rust/packages-creates-modules.md)
- [🏘️ Vectors](./rust/vectors.md)
- [🧵 Strings](./rust/strings.md)

### 🤖 AI & Machine Learning

- [Math with Pytorch](./ai-ml/math-with-pytorch.md)

### 🎨 Design

- [🖌️ Design System](./design/design-system.md)
- [🌈 Color Tokens](./design/color-tokens.md)

## 📝 Note Guidelines

- Note should follow this structure:
  - Start with `#` for the title of the note
  - Display the table of contents
  - `## 👀 Fast Lookup` should be the first section
    - This section serve as a quick reference cheat-sheet which may(not necessarily) include:
      - **Key definitions**: Core concepts in bullet points (e.g., "Vector is a growable array")
      - **Essential syntax**: Critical code snippets for creation/usage (e.g., `Vec::new()`, `vec![1,2,3]`)
      - **Important characteristics**: Key properties and behaviors of the concept
      - **Core methods/operations**: Most commonly used functionality with minimal context
      - **Critical distinctions**: Key differences between related or similar concepts
      - **Quick reminders**: When and why to use the concept
  - ... Extra more sections as needed
- Add **Relatable Emoji** to the head of the section titles (`#`, `##`, `###` only)
- Split the topic if it's too long
