# 🔄 Iterables and Iterators

- [🔄 Iterables and Iterators](#-iterables-and-iterators)
  - [👀 Fast Lookup](#-fast-lookup)
  - [🤔 What are they?](#-what-are-they)
  - [⚡ When and How to use them?](#-when-and-how-to-use-them)

## 👀 Fast Lookup

- **Iterable**: Object that can be iterated over (lists, tuples, strings, dicts, sets)
- **Iterator**: Object representing a stream of data with `__iter__()` and `__next__()` methods
- **`__iter__()`**: Returns the iterator object itself
- **`__next__()`**: Returns next item or raises `StopIteration`
- **`iter()`**: Built-in function to get iterator from iterable
- **`next()`**: Built-in function to get next value from iterator
- **Iterator is like a pointer**: Points to current element in collection

## 🤔 What are they?

- **Iterable**: An object that can be iterated over. Examples include lists, tuples, strings, dictionaries, and sets.
- **Iterator**: An object that represents a stream of data. It returns one element at a time from a collection when `next()` is called on it. An iterator must implement the `__iter__()` and `__next__()` methods.

- `__iter__()` : This method returns the iterator object itself. It is required to make an object iterable.
- `__next__()` : This method returns the next item from the collection. If there are no more items, it raises the `StopIteration` exception.

So Iterator is kind of a **pointer** to the current element in the collection.

## ⚡ When and How to use them?

Iterables and iterators are used when you want to iterate over a collection of items. They are used in loops, comprehensions, and generators.

```python
# Example using a custom iterator
class Numbers:
  def __init__(self, start, end):
    self.start = start
    self.end = end
  
  def __iter__(self):
    return self
  
  def __next__(self):
    if self.start >= self.end:
      raise StopIteration
    current = self.start
    self.start += 1
    return current

# Using the iterator
numbers = Numbers(1, 5)
for num in numbers:
  print(num)  # Prints 1, 2, 3, 4

# Using iter() and next()
my_list = [1, 2, 3]
iterator = iter(my_list)
print(next(iterator))  # Prints 1
print(next(iterator))  # Prints 2
print(next(iterator))  # Prints 3
```
