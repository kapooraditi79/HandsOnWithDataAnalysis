# Introduction To Numpy

Numpy short for Numerical Python, is the bedrock of so many other libraries in Python like pandas, matplotlib, scikit-learn.

Numpy is the foundation on which the entire data analysis is built. It is the most important and versatile library. It stands for **_""n-dimensional array""._**

The role of it is to provide support for large multidimensional arrays and matrices. And also to Mathematical Functions.

## n-dimensional Numpy array

```python
numpy_array = np.array([1, 2, 3, 4, 5])
print(numpy_array)
```

_Check out the app_01.ipynb for better understanding._

## Built-In Functions In Numpy

Numpy offers built-in functions with the help of which you basically thrive in doing your data analysis.

- `np.random()`: Generates arrays with random values.
- `np.linspace()`: Creates an array with a specified number of evenly spaced values.
- `np.arange()`: Creates an array with a range of values.
- `np.ones()`: Creates an array filled with ones.
- `np.zeros()`: Creates an array filled with zeros.

Example:

```python
shape = (3, 4)
zeros_array = np.zeros(shape)
print("Zeros Array:")
print(zeros_array)
```

_Check out the app_01.ipynb for more examples._

## Indexing and Slicing

The accessing of individual elements or a subarray of elements within an array is indexing and slicing. _(Fun fact: where there is colons-> it is slicing. otherwise it is indexing)_

**Basic Indexing**: Allows you to access individual elements

**Slicing Arrays**: Allows you to create subarrays with the format of `start:stop:step` . It is exclusive of the stop. That means the index you put at `stop`, that position element will not be included in the subarray.

by default `step` value is 1.

**Boolean Indexing:** Selects elements from an array based on a condition. Effectively it creates a `True/False` mark. Selecting the elements where it is `True`.

**Fancy Indexing:** Allows to access multiple elements of an array simultaneously.

## Reshaping and Resizing

Reshape: You change the shape (dimensions) of an array without changing its data.

Resize: Resize, unlike reshape, can alter the total number of elements in the array. It changes the shape and size of an array in-place. It is important to use resize with caution as it can lead to unexpected behavior if not used carefully.

syntax for resize:

`numpy.resize(a, new_shape)`

`a`: The input array that needs to be resized.

`new_shape`: The desired total number of elements in the resized array.

## Ravel and Flatten

_Ravel_ : Creates a one-dimensional view of the original array. Any modifications made to the one-dimensional view will be reflected in the original array (they share the same underlying data).

_Flatten_ : Similar to ravel, but it returns a copy of the original array flattened into 1D. Changes to the flattened copy won't affect the original array.
