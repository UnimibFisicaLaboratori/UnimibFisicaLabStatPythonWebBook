# Notable Python Libraries

## NumPy

![NumPy logo](https://numpy.org/images/twitter-image.jpg)

```{epigraph}
"The fundamental package for scientific computing with Python"

-- [NumPy.org](https://numpy.org)
```

[NumPy](https://numpy.org) is the fundamental package for scientific computing in Python.
It is a Python library that provides a multidimensional array object (`numpy.ndarray`), various derived objects such as masked arrays and matrices, and an assortment of routines for fast operations on arrays.

To start using NumPy, simply import the library, usually with the abbreviation `np`:

```python
import numpy as np
```

The main difference between the `ndarray` and Python `list` is that `ndarray` has fixed size after declaration.
It does not mean that the addition of elements is forbidden, but it does technically require the creation of a new array and the destruction of the starting one.

```{note}
Given the memory management operations involved when adding a new element to a `ndarray`, it is best to create the `ndarray` just before using it and fill a Python `list` if loops are involved (see the example {ref}`examples:numpy:ndarray`).

```python
x = []
for i in range(10):
  x += [i]
x = np.array(x)
```

(**n.b.**: NumPy array types, while being named `ndarray`, are called with `numpy.array()`)

This small constraint on the array manipulation makes a great difference in numeric operations among the arrays, since the fixed size allows the interpreter to use routines that, in the backbone of NumPy, are coded in *C* or *fortran*, with a much faster execution time than Python.
The performance difference is shown in the example {ref}`examples:numpy:ndarray_operations`, where a element-wise multiplication between two arrays is performed using built-in Python lists and NumPy arrays. 

```python
x, y = list(range(10000)), list(range(10000))
X, Y = np.array(x), np.array(y)
# lists multiplication
z = [ x[i]*y[i] for i in range(len(x)) ]
# ndarray multiplication
Z = X*Y
```

In addition to being much simpler and clear to write, the NumPy arrays multiplication is 10x faster for arrays of 10k entries and 20x faster for arrays of 1M entries.

### Multidimensional arrays

The `ndarray` can also be multidimensional

```python
>>> A = np.array([[1,2,3],[4,5,6]])
>>> A
array([[1, 2, 3],
       [4, 5, 6]])
>>> A.shape
(2, 3)
```

It can also be reshaped

```python
A.reshape(3,2)
>>> A.reshape(3,2)
array([[1, 2],
       [3, 4],
       [5, 6]])
```

`````{warning}
The `reshape` function does not modify the original array. 
One needs to store it to a new object:
```python
B = A.reshape(3,2)
```
`````

To access its elements

```python
>>> # row-wise
>>> A[1]
array([4, 5, 6])
>>> # row+column-wise
>>> A[1,2]
6
```

```{note}
Accessing the array elements with `A[1,2]` is faster than `A[1][2]` since the latter involves the creation in memory of another array.
```

## Linear Algebra with NumPy arrays

Particularly helpful functions are available in NumPy for linear algebra.
Multidimensional arrays can indeed be considered as matrices and vectors, and NumPy provides various optimised functions to perform operations amongst them.

### Matrix operations

Supposing to have a 2x2 matrix

$$
A = \begin{pmatrix}
  1 & 2 \\
  4 & 5 \\
\end{pmatrix}
$$

```python
>>> A = np.array([[1,2],[4,5]])
>>> A
```

let's see what operations NumPy allows us to perform.

#### Multiplication

We can multiply the matrix to a number with the `*` operator.
This performs an element-wise multiplication.

```python
>>> 2*A
array([[ 2,  4],
       [ 8, 10]])
```

or perform correct vector and matrix multiplication with [`numpy.dot`](https://numpy.org/doc/stable/reference/generated/numpy.dot.html#numpy-dot)

```python
>>> B = np.array([3,6])
>>> np.dot(A,B)
array([15, 42])
>>> C = np.array([[1,2,3],[4,5,6]])
>>> np.dot(A,C)
array([[ 9, 12, 15],
       [24, 33, 42]])
```

The inner product of two vectors $\vec{a}\cdot\vec{b}$ is calculated with [`numpy.inner`](https://numpy.org/doc/stable/reference/generated/numpy.inner.html#numpy-inner)

```python
>>> a = np.array([1,2,3])
>>> b = np.array([4,5,6])
>>> np.inner(a,b)
32
```

The outer (cross) product of two vectors $\vec{a}\times\vec{b}$ is calculated with [`numpy.outer`](https://numpy.org/doc/stable/reference/generated/numpy.inner.html#numpy-inner)

```python
>>> np.outer(a,b)
array([[ 4,  5,  6],
       [ 8, 10, 12],
       [12, 15, 18]])
```

#### Transpose

The matrix can be transposed with [`numpy.transpose`](https://numpy.org/doc/stable/reference/generated/numpy.transpose.html#numpy-transpose)

```python
>>> tA = np.transpose(A)
>>> tA
array([[1, 4],
       [2, 5]])
```

#### Determinant

We can calculate its determinant with [`numpy.linalg.det`](https://numpy.org/doc/stable/reference/generated/numpy.linalg.det.html#numpy-linalg-det)

```python
>>> A = np.array([[1,2],[4,5]])
>>> A
array([[1, 2],
       [4, 5]])
>>> np.linalg.det(A)
-2.9999999999999996
```

```{note}
The output of `np.linalg` is limited by the machine precision. If you know that the result is an integer like in the case above, you can cast the result with `int(np.linalg.det(A))`
```

#### Inverse

Since the determinant is non-zero, we can invert the matrix with [`numpy.linalg.inv`](https://numpy.org/doc/stable/reference/generated/numpy.linalg.inv.html#numpy-linalg-inv)

```python
>>> invA = np.linalg.inv(A)
>>> invA
array([[-1.66666667,  0.66666667],
       [ 1.33333333, -0.33333333]])
```

#### Diagonal

The diagonal of the matrix is given by

```python
>>> diagA = np.diag(A)
array([1, 5])
```

#### Conjugate

Supposing to have a matrix with complex elements, we can get the conjugate matrix with [`np.conjugate`](https://numpy.org/doc/stable/reference/generated/numpy.conjugate.html#numpy-conjugate)

```python
>>> C = np.array([[1,5j],[2+3j,0.5-0.8j]])
>>> C
array([[1. +0.j , 0. +5.j ],
       [2. +3.j , 0.5-0.8j]])
>>> np.conjugate(C)
array([[1. -0.j , 0. -5.j ],
       [2. -3.j , 0.5+0.8j]])
```

### Special arrays declarations

NumPy has various shortcuts to define special arrays.
#### 1-D arrays

An array with integers spanning two values in step is defined with [`numpy.arange`](https://numpy.org/doc/stable/reference/generated/numpy.arange.html#numpy.arange)

```python
>>> r = np.arange(1,8,2)
>>> r
array([1, 3, 5, 7])
>>> r = np.arange(10)
>>> r
array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
```

An array of a specific number of elements spaced equally is defined by [`numpy.linspace`](https://numpy.org/doc/stable/reference/generated/numpy.linspace.html#numpy.linspace)

```python
>>> x = np.linspace(0,1,11)
>>> x
array([0. , 0.1, 0.2, 0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 0.9, 1. ])
```

#### 2-D arrays

The identity matrix can be created with [`numpy.eye`](https://numpy.org/doc/stable/reference/generated/numpy.eye.html#numpy.eye)

```python
>>> I = np.eye(3)
>>> I
array([[1., 0., 0.],
       [0., 1., 0.],
       [0., 0., 1.]])
```

It is possible to create a diagonal matrix with [`numpy.diag`](https://numpy.org/doc/stable/reference/generated/numpy.diag.html#numpy.diag)

```python
>>> d
array([[1, 0, 0],
       [0, 2, 0],
       [0, 0, 3]])
```

#### n-D arrays

A ndarray of size *n* filled with zeros is given by

```python
>>> z = np.zeros(5)
>>> z
array([0., 0., 0., 0., 0.])
>>> z = np.zeros((2,3))
>>> z
array([[0., 0., 0.],
       [0., 0., 0.]])
```

Similarly, for a ndarray filled with ones (or any given number)

```python
>>> o = np.ones(5)
>>> o
array([1., 1., 1., 1., 1.])
>>> 6.2*np.ones(5)
array([6.2, 6.2, 6.2, 6.2, 6.2])
>>> o = np.ones( (2,3) )
>>> o
array([[1., 1., 1.],
       [1., 1., 1.]])
```

### Example: Vector Calculus
 ? Exercise: Least Squares with matrix inversion for f(x) = A + Bx

## SciPy

[`SciPy`](https://scipy.org) is a library providing algorithms and data structures for scientific computing.

### Example: Calculate a p-value

## Examples

A notebook with the examples proposed in this lecture can be found [here](../examples/python_libraries_examples.ipynb)


## NOTES

List of subjects that will be useful in the future
  * numpy universal functions https://numpy.org/doc/stable/reference/ufuncs.html
  