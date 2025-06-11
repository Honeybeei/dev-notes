# ⚡ Lambda Functions

- [⚡ Lambda Functions](#-lambda-functions)
  - [👀 Fast Lookup](#-fast-lookup)
  - [❓ What is a Lambda Function?](#-what-is-a-lambda-function)
  - [📚 Basic Syntax](#-basic-syntax)
  - [🔄 Lambda vs Regular Functions](#-lambda-vs-regular-functions)
  - [🎯 Common Use Cases](#-common-use-cases)
    - [🗂️ With `map()`](#️-with-map)
    - [🔽 With `filter()`](#-with-filter)
    - [📊 With `sorted()`](#-with-sorted)
  - [⚠️ Limitations](#️-limitations)

## 👀 Fast Lookup

- **Lambda functions**: Anonymous functions defined with `lambda` keyword
- **Syntax**: `lambda arguments: expression`
- **Single expression**: Can only contain one expression, no statements
- **Return value**: Automatically returns the result of the expression
- **Common use**: With `map()`, `filter()`, `sorted()`, `reduce()`
- **No name**: Anonymous, but can be assigned to variables
- **Limitations**: No statements, no multiple lines, no docstrings

## ❓ What is a Lambda Function?

Lambda functions are small, anonymous functions that can be defined inline. They are a concise way to create simple functions without using the `def` keyword.

## 📚 Basic Syntax

```python
# Basic lambda syntax
lambda arguments: expression

# Example: Square a number
square = lambda x: x ** 2
print(square(5))  # Output: 25

# Multiple arguments
add = lambda x, y: x + y
print(add(3, 4))  # Output: 7

# No arguments
greeting = lambda: "Hello, World!"
print(greeting())  # Output: Hello, World!
```

## 🔄 Lambda vs Regular Functions

```python
# Regular function
def multiply(x, y):
    return x * y

# Lambda function
multiply_lambda = lambda x, y: x * y

# Both work the same way
print(multiply(3, 4))        # Output: 12
print(multiply_lambda(3, 4)) # Output: 12
```

## 🎯 Common Use Cases

### 🗂️ With `map()`

```python
# Square all numbers in a list
numbers = [1, 2, 3, 4, 5]
squared = list(map(lambda x: x ** 2, numbers))
print(squared)  # Output: [1, 4, 9, 16, 25]

# Convert strings to uppercase
names = ["alice", "bob", "charlie"]
upper_names = list(map(lambda name: name.upper(), names))
print(upper_names)  # Output: ['ALICE', 'BOB', 'CHARLIE']
```

### 🔽 With `filter()`

```python
# Filter even numbers
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
evens = list(filter(lambda x: x % 2 == 0, numbers))
print(evens)  # Output: [2, 4, 6, 8, 10]

# Filter strings longer than 5 characters
words = ["apple", "banana", "cherry", "date", "elderberry"]
long_words = list(filter(lambda word: len(word) > 5, words))
print(long_words)  # Output: ['banana', 'cherry', 'elderberry']
```

### 📊 With `sorted()`

```python
# Sort tuples by second element
students = [("Alice", 85), ("Bob", 90), ("Charlie", 78)]
sorted_by_grade = sorted(students, key=lambda student: student[1])
print(sorted_by_grade)  # Output: [('Charlie', 78), ('Alice', 85), ('Bob', 90)]

# Sort strings by length
words = ["python", "java", "c", "javascript"]
sorted_by_length = sorted(words, key=lambda word: len(word))
print(sorted_by_length)  # Output: ['c', 'java', 'python', 'javascript']
```

## ⚠️ Limitations

- **Single expression only**: Cannot contain statements like `print`, `return`, `if` statements
- **No multiple lines**: Must fit on a single line
- **No docstrings**: Cannot include documentation
- **Less readable**: For complex logic, regular functions are better

```python
# ❌ This won't work - contains statements
# invalid_lambda = lambda x: print(x); return x

# ✅ Use regular functions for complex logic
def complex_function(x):
    """This function does something complex."""
    if x > 0:
        print(f"Positive: {x}")
        return x * 2
    else:
        print(f"Non-positive: {x}")
        return 0
```
