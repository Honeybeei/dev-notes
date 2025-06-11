# 📘 User Input and Output

- [📘 User Input and Output](#-user-input-and-output)
  - [👀 Fast Lookup](#-fast-lookup)
  - [🎤 Taking Input from the User](#-taking-input-from-the-user)
    - [🔤 Using the `input()` Function](#-using-the-input-function)
    - [🔢 Handling Different Data Types](#-handling-different-data-types)
    - [✅ Best Practices for Handling Input](#-best-practices-for-handling-input)
    - [🚀 Advanced Input Techniques](#-advanced-input-techniques)
  - [💁 Displaying Output to the User](#-displaying-output-to-the-user)
    - [🖨️ Using the `print()` Function](#️-using-the-print-function)
    - [📝 Formatted Output (f-strings)](#-formatted-output-f-strings)
    - [🔀 Working with Multiple Outputs](#-working-with-multiple-outputs)
    - [◀️ Carriage Return (`\r`) and Backspace (`\b`)](#️-carriage-return-r-and-backspace-b)
    - [Carriage Return (`\r`)](#carriage-return-r)
    - [Backspace (`\b`)](#backspace-b)

## 👀 Fast Lookup

- **`input()`**: Get user input as string
- **Type conversion**: Use `int()`, `float()` to convert string input
- **Error handling**: Use `try-except` for input validation
- **`print()`**: Display output to user
- **f-strings**: `f"Hello {name}"` for formatted output
- **`sep` parameter**: Control separator in `print()`
- **`end` parameter**: Control what prints at end (default: newline)
- **`\r` (carriage return)**: Move cursor to start of line
- **`\b` (backspace)**: Move cursor one position back

## 🎤 Taking Input from the User

### 🔤 Using the `input()` Function

In Python, we can receive input from the user using the built-in `input()` function. It captures everything the user types as a string.

```python
name = input("What's your name? ")
print(f"Hello, {name}!")
```

> **Note**: The `input()` function always returns a string. To work with different data types, you need to convert the input.

### 🔢 Handling Different Data Types

When you want to work with numbers, you'll need to convert the string input into the appropriate data type, like `int()` or `float()`.

```python
age = input("Enter your age: ")  # User input as a string
age = int(age)  # Convert to integer
print(f"You are {age} years old.")
```

### ✅ Best Practices for Handling Input

- **Error Handling**: Since user input can be unpredictable, it's a good practice to handle conversion errors using `try-except`.

```python
try:
    age = int(input("Enter your age: "))
except ValueError:
    print("Please enter a valid number!")
```

- **Validation**: You can validate input before conversion to make sure it meets certain conditions (like only containing digits).

```python
age = input("Enter your age: ")
if age.isdigit():
    age = int(age)
else:
    print("Please enter a valid number!")
```

### 🚀 Advanced Input Techniques

For scenarios where multiple inputs are required at once, you can split the input string:

```python
data = input("Enter your name, age, and city (comma-separated): ")
name, age, city = data.split(",")  # Splitting the input based on commas
age = int(age)  # Convert age to an integer
print(f"Name: {name}, Age: {age}, City: {city}")
```

This approach is helpful for parsing structured input from users.

## 💁 Displaying Output to the User

### 🖨️ Using the `print()` Function

The `print()` function is used to display information back to the user. It can accept multiple arguments, and by default, separates them with spaces:

```python
print("Hello,", "World!")  # Output: Hello, World!
```

You can also print variables and static strings together:

```python
name = "Alice"
print("Hello,", name)  # Output: Hello, Alice
```

### 📝 Formatted Output (f-strings)

To create more sophisticated and readable outputs, use **f-strings**, introduced in Python 3.6. They allow embedding expressions inside string literals using curly braces `{}`.

```python
name = "Alice"
age = 30
print(f"{name} is {age} years old.")  # Output: Alice is 30 years old.
```

You can also use expressions inside f-strings:

```python
x = 10
y = 20
print(f"The sum of {x} and {y} is {x + y}.")
```

### 🔀 Working with Multiple Outputs

You can use the `sep` and `end` parameters of the `print()` function for advanced formatting:

- **sep**: Defines how to separate multiple values in a `print()` statement.
- **end**: Defines what to print at the end of the output (by default, it’s a newline).

```python
print("apple", "banana", "cherry", sep=", ")  # Output: apple, banana, cherry
print("Hello", end="!")  # Output: Hello!
```

### ◀️ Carriage Return (`\r`) and Backspace (`\b`)

### Carriage Return (`\r`)

- **Function:** Moves the cursor back to the start of the current line without advancing downward.
- **Common Use:** Often used in terminal outputs to overwrite content on the same line.
  - For example, using `print("Loading\rDone")` might first print `Loading` and then use `\r` to return the cursor to the start of the line and then print `Done` over it.  
  - Result on the screen:  

    ```Plain Text
    Done
    ```

    (instead of two separate lines)

### Backspace (`\b`)

- **Function:** Moves the cursor one character position backwards.
- **Common Use:** Erase or overwrite previously printed characters on the same line.
  - For example, `print("Hello\b", end="")` prints `Hello` and then moves back one space, so if you print another character immediately after, it will overwrite the last character of `Hello`.
  - If you follow with `print("a", end="")`, the result on the screen would be:

    ```Plain Text
    Hella
    ```

    (the `o` is replaced by `a`)


```python
print("Loading...", end="\r")
```
