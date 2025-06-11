# 🎯 Function Arguments

- [🎯 Function Arguments](#-function-arguments)
  - [👀 Fast Lookup](#-fast-lookup)
  - [📍 Positional Arguments](#-positional-arguments)
  - [🏷️ Keyword Arguments](#️-keyword-arguments)
  - [💫 Default Arguments](#-default-arguments)
  - [📦 Variable-Length Arguments](#-variable-length-arguments)
    - [✨ `*args`](#-args)
    - [🗝️ `**kwargs`](#️-kwargs)
  - [📭 Unpacking Arguments](#-unpacking-arguments)
  - [🔄 Combining Arguments](#-combining-arguments)
  - [🔄 Argument Passing](#-argument-passing)
    - [🔒 Passing Immutable Objects](#-passing-immutable-objects)
    - [🔓 Passing Mutable Objects](#-passing-mutable-objects)

## 👀 Fast Lookup

- **Positional Arguments**: Arguments passed by order/position
- **Keyword Arguments**: Arguments passed by name (order doesn't matter)
- **Default Arguments**: Arguments with default values
- **`*args`**: Accept variable number of positional arguments (tuple)
- **`**kwargs`**: Accept variable number of keyword arguments (dict)
- **Argument Order**: positional → `*args` → keyword → `**kwargs`
- **Immutable objects**: passed by value (changes don't affect original)
- **Mutable objects**: passed by reference (changes affect original)

## 📍 Positional Arguments

- The most common way to pass arguments to a function.
- The **order** of the arguments is important.

```python
def add_numbers(a, b):
  return a + b

print(add_numbers(3, 5)) # 8
```

## 🏷️ Keyword Arguments

- The arguments are passed by their names.
- The order of the arguments is not important.

```python
def add_numbers(a, b):
  return a + b

print(add_numbers(a=3, b=5)) # 8
print(add_numbers(b=5, a=3)) # 8
```

## 💫 Default Arguments

- Default values are assigned to the arguments.
- If the argument is not passed, the default value is used.

```python
def say_hello(name='World'):
  return f'Hello, {name}!'

print(say_hello()) # Hello, World!
print(say_hello("Honeybeei")) # Hello, Honeybeei!
```

## 📦 Variable-Length Arguments

### ✨ `*args`

- The `*args` parameter allows the function to accept any number of positional arguments.

```python
def say_hello_to_everyone(*names):
    print(type(names))  # <class 'tuple'>
    for name in names:
        print(f"Hello, {name}!")


say_hello_to_everyone("Alice", "Bob", "Charlie")
# <class 'tuple'>
# Hello, Alice!
# Hello, Bob!
# Hello, Charlie!
```

### 🗝️ `**kwargs`

- The `**kwargs` parameter allows the function to accept any number of keyword(key-value) arguments.

```python
def print_person_info(**person):
  print(type(person))  # <class 'dict'>
  for key, value in person.items():
    print(f'{key}: {value}')

print_person_info(name='Honeybeei', age=29, city='Hamburg')
# <class 'dict'>
# name: Honeybeei
# age: 29
# city: Hamburg
```

## 📭 Unpacking Arguments

- The `*` operator can be used to unpack the elements of a list or tuple into the arguments of a function.

```python
def add_numbers(a, b):
  return a + b

numbers = [3, 5]
print(add_numbers(*numbers)) # 8
```

- The `**` operator can be used to unpack the elements of a dictionary into the keyword arguments of a function.

```python
def print_person_info(name, age, city):
  print(f'Name: {name}')
  print(f'Age: {age}')
  print(f'City: {city}')

person = {'name': 'Honeybeei', 'age': 29, 'city': 'Hamburg'}
print_person_info(**person)
# Name: Honeybeei
# Age: 29
# City: Hamburg
```

## 🔄 Combining Arguments

- The order of the arguments should be:
  - Positional arguments
  - `*args`
  - Keyword arguments
  - `**kwargs`

```python
def greet(greeting, *names, age=25, **details):
  for name in names:
    print(f"{greeting}, {name}!")
  print(f"Age: {age}")
  for key, value in details.items():
    print(f"{key}: {value}")

# Usage
greet("Hello", "Honeybeei", "Bob", age=30, city="Hamburg", hobby="Reading")

# Output
# Hello, Honeybeei!
# Hello, Bob!
# Age: 30
# city: Hamburg
# hobby: Reading
```

## 🔄 Argument Passing

### 🔒 Passing Immutable Objects

- Immutable Objects(Numbers, Strings, Tuples) are **passed by value**.
- Which means the value of the argument is copied to the function.
- The changes made to the argument inside the function do not affect the original object.

```python
def change_number(number):
  number += 10
  return number

num = 5
print(change_number(num)) # 15
print(num) # 5
```

### 🔓 Passing Mutable Objects

- Mutable Objects(Lists, Dictionaries, Sets) are **passed by reference**.
- Which means the reference(address) of the object is passed to the function.
- The changes made to the argument inside the function affect the original object.

```python
def add_element_to_list(lst):
  lst.append(4)
  return lst

numbers = [1, 2, 3]
print(add_element_to_list(numbers)) # [1, 2, 3, 4]
print(numbers) # [1, 2, 3, 4]
```
