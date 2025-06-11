# 🔄 Generators

- [🔄 Generators](#-generators)
  - [👀 Fast Lookup](#-fast-lookup)
  - [❓ What is a Generator?](#-what-is-a-generator)
  - [🔄 What is the difference between a Generator and a Normal Function?](#-what-is-the-difference-between-a-generator-and-a-normal-function)
  - [⚙️ How does it work?](#️-how-does-it-work)

## 👀 Fast Lookup

- **Generators**: Special functions that can pause and resume execution
- **`yield`**: Keyword that makes a function a generator (instead of `return`)
- **Memory-efficient**: Produce values on-demand, not all at once
- **State preservation**: Function state is saved between `yield` calls
- **Lazy evaluation**: Values are generated only when needed
- **Iterator-like**: Can be used with `next()` and `for` loops
- **`StopIteration`**: Raised when generator is exhausted

## ❓ What is a Generator?

- Generator is a special type of function that can pause its execution and resume it later.
- Instead of returning a single value (like normal functions), generators yield multiple values, one at a time, as you iterate through them.
- They are memory-efficient because they don't construct the entire result in memory at once; they produce results on-the-fly.

In my perspective of understanding, it can be simulated like this in C:

```c
#include <stdio.h>

int* generator(int n) {
  static int i = 0;
  static int arr[10];
  for (i = 0; i < n; i++) {
    arr[i] = i;
  }
  return arr; 
}

int main() {
  int* gen = generator(10);
  for (int i = 0; i < 10; i++) {
    printf("%d\n", gen[i]);
  }
  return 0;
}
```

## 🔄 What is the difference between a Generator and a Normal Function?

- Normal functions return a single value using `return` statement, whereas generators yield multiple values using `yield` statement.
- Each time `yield` is hit, the state of the generator function is **saved** so that it can resume from where it left off on the next iteration.

```python
def count_up_to(n):
  count = 1
  while count <= n:
    yield count # Pause here to yield the current value
    count += 1

counter = count_up_to(5)
print(next(counter)) # 1
for number in counter:
  print(number) # 2, 3, 4, 5
```

## ⚙️ How does it work?

- When you call a generator function, it returns a generator object without executing the function. (Generators are like iterators)
- When we call `next()` (iterate) on the generator object, the function starts executing until it hits a `yield` statement.
- The value of the `yield` statement is returned to the caller and the state of the function is saved.
- The next time `next()` is called, the function resumes execution from where it left off.
- When the function hits `return` or reaches the end of the function, `StopIteration` exception is raised.
- You can also use a `for` loop to iterate through the generator object.
