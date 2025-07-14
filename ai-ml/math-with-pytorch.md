# Math with Pytorch

- [Math with Pytorch](#math-with-pytorch)
  - [👀 Fast Lookup](#-fast-lookup)
  - [Data Types](#data-types)
  - [Matrix Operations](#matrix-operations)
    - [Transpose Operation](#transpose-operation)
    - [Dot Product](#dot-product)
    - [Matrix Multiplication](#matrix-multiplication)

## 👀 Fast Lookup

## Data Types

- **Scalar**: A single number.

- **Vector**: An array of numbers, which can be represented as a point in space
  - **Row Vector**: A 1 x n (horizontal) matrix, where n is the number of elements.
  - **Column Vector**: An n x 1 (vertical) matrix, where n is the number of elements.

- **Matrix**: A 2D array of numbers, which can be thought of as a collection of vectors.
- **Tensor**: A multi-dimensional array of numbers, which generalizes vectors and matrices to higher dimensions.

| Math | "Scalar" | "Vector" | "Matrix" | "Tensor" |
|-------|----------|----------|----------|----------|
| Numpy | "Array" | "Array" | "ND Array" | "ND Array" |
| Pytorch | "Tensor" | "Tensor" | "Tensor" | "Tensor" |

## Matrix Operations

### Transpose Operation
  
- **Transpose**: Flips a matrix over its diagonal, converting rows to columns and vice versa.
  - **Transpose Notation**: If A is a matrix, then A^T denotes its transpose.
  - **Example**: If A = [[1, 2], [3, 4]], then A^T = [[1, 3], [2, 4]].

```python
import numpy as np
# Create a matrix
array = np.array([[1, 2], [3, 4]])
# Transpose the matrix
transposed = array.T # [[1, 3], [2, 4]]
```

```python
import torch
# Create a matrix
tensor = torch.tensor([[1, 2], [3, 4]])
# Transpose the matrix
transposed = tensor.t() # [[1, 3], [2, 4]]
```

### Dot Product

The dot product of two vectors is the sum of the products of their corresponding elements. The result is a scalar.

- **Dot Product Notation**: `α = a ⋅ b = <a, b> = a^T b = Σ(a_i * b_i)`
- **Example**: If `a = [1, 2, 3]` and `b = [4, 5, 6]`, then `a · b = (1*4) + (2*5) + (3*6) = 4 + 10 + 18 = 32`.

```python
import numpy as np
# Create two vectors
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])
# Calculate the dot product
dot_product = np.dot(a, b)
print(dot_product) # 32
```

```python
import torch
# Create two vectors
a = torch.tensor([1, 2, 3])
b = torch.tensor([4, 5, 6])
# Calculate the dot product
dot_product = torch.dot(a, b)
print(dot_product) # tensor(32)
```

### Matrix Multiplication

...