# Introduction to NumPy

**NumPy** (Numerical Python) is a powerful Python library used for numerical and scientific computing. It provides support for **multidimensional arrays**, **mathematical functions**, and various tools for working with these arrays. It is one of the foundational libraries in Python for data science and machine learning.

## Table of Contents
- [Key Features](#key-features)
- [NumPy Arrays](#numpy-arrays)
- [Array Operations](#array-operations)
- [Array Indexing and Slicing](#array-indexing-and-slicing)
- [Mathematical Functions](#mathematical-functions)
- [Reshaping and Resizing](#reshaping-and-resizing)

## Key Features
1. **Multidimensional Arrays**: NumPy provides the `ndarray`, a fast and efficient multi-dimensional array.
2. **Mathematical Functions**: Offers optimized mathematical functions like trigonometry, statistics, linear algebra, etc.
3. **Vectorized Operations**: Operations in NumPy are **vectorized**, which makes computations faster by avoiding loops.
4. **Broadcasting**: NumPy allows operations between arrays of different shapes, automatically expanding smaller arrays to match larger ones.


## NumPy Arrays
The core of NumPy is the **ndarray** (n-dimensional array). You can create arrays in several ways:
1) Creating Arrays
```python
import numpy as np

# Creating a 1D array
arr = np.array([1, 2, 3, 4])
print(arr)

# Creating a 2D array
arr_2d = np.array([[1, 2], [3, 4]])
print(arr_2d)
```
2) Other Array Creations
```python
# Array of zeros
zeros_arr = np.zeros((3, 3))
# Array of ones
ones_arr = np.ones((2, 4))
# Array of a range of numbers
range_arr = np.arange(0, 10, 2)
# Array of random numbers
random_arr = np.random.rand(3, 3)
```


## Array Operations
NumPy arrays support a variety of operations, including element-wise arithmetic:
- Arithmetic Operations
```python
arr = np.array([1, 2, 3, 4])

# Add 5 to each element
arr_plus_five = arr + 5

# Multiply each element by 2
arr_mult_two = arr * 2

# Element-wise addition of two arrays
arr1 = np.array([1, 2, 3])
arr2 = np.array([4, 5, 6])
arr_sum = arr1 + arr2

# Element-wise multiplication
arr_prod = arr1 * arr2
```


## Array Indexing and Slicing
Just like lists in Python, NumPy arrays can be indexed and sliced to access elements or subarrays. You can use both positive and negative indexing.
- indexing
```python
import numpy as np

arr = np.array([10, 20, 30, 40])

# Access the first element
print(arr[0])  # Output: 10
# Access the last element
print(arr[-1])  # Output: 40
# 2D Array indexing
arr_2d = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
# Access an element from the second row and third column
print(arr_2d[1, 2])  # Output: 6
```

- slicing
```python
# 1D array slicing
arr = np.array([10, 20, 30, 40, 50])

# Slice elements from index 1 to 3
print(arr[1:4])  # Output: [20 30 40]

# Slice and modify
arr[1:3] = [200, 300]
print(arr)  # Output: [ 10 200 300  40  50]

# 2D array slicing
arr_2d = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
# Get the first two rows and the first two columns
print(arr_2d[:2, :2])  # Output: [[1 2]
                       #          [4 5]]
```

## Mathematical Functions
- Common Mathematical Functions
```python
# Basic arithmetic
arr = np.array([1, 2, 3, 4])

# Square root
print(np.sqrt(arr))  # Output: [1. 1.414 1.732 2.]

# Exponentiation
print(np.exp(arr))  # Output: [ 2.718  7.389 20.085 54.598]

# Trigonometric functions
angles = np.array([0, np.pi/2, np.pi])
print(np.sin(angles))  # Output: [0. 1. 0.]

# Summing the array
print(np.sum(arr))  # Output: 10

# Mean and standard deviation
print(np.mean(arr))  # Output: 2.5
print(np.std(arr))  # Output: 1.118
```

- Matrix Operations
```python
# Matrix multiplication (dot product)
arr_2d_1 = np.array([[1, 2], [3, 4]])
arr_2d_2 = np.array([[5, 6], [7, 8]])

product = np.dot(arr_2d_1, arr_2d_2)
print(product)  # Output: [[19 22]
               #          [43 50]]
```

## Reshaping and Resizing
- Reshaping Arrays
```python
arr = np.array([1, 2, 3, 4, 5, 6])

# Reshape into a 2x3 matrix
reshaped_arr = arr.reshape(2, 3)
print(reshaped_arr)
# Output:
# [[1 2 3]
#  [4 5 6]]

# Reshape a 3D array
reshaped_3d = np.array(range(12)).reshape(2, 3, 2)
print(reshaped_3d)
# Output:
# [[[ 0  1]
#   [ 2  3]
#   [ 4  5]]
#  [[ 6  7]
#   [ 8  9]
#   [10 11]]]
```

- Resizing Arrays
```python
arr = np.array([1, 2, 3, 4])

# Resize the array to 2x3 (adds extra elements or truncates)
resized_arr = np.resize(arr, (2, 3))
print(resized_arr)
# Output:
# [[1 2 3]
#  [4 1 2]]  # Elements repeat if size increases

# Resizing an array into a smaller one
resized_arr = np.resize(arr, (2, 2))
print(resized_arr)
# Output:
# [[1 2]
#  [3 4]]
```