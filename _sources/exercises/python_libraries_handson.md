# Notable Python Libraries - Hands On

## NumPy

### `ndarray` multiplication

Write a script that calculates the performance improvement (time-wise) when multiplying arrays of $n=10^i$ elements, with $i=0,1,...,7$.
Estimate the performance improvement using a function that depends on the number of elements of the arrays.
The output of the script should be a sequence that prints the performance improvement corresponding to each considered array size.

`````{hint}
Prototype the function as
```python
def ndarray_vs_list_performance_gain(n):
    """Calculates the time-wise performance gain of a multiplication of two arrays of $n$ elements 

    Args:
        n (int): the size of the array

    Returns:
        float: the time gain
    """    
    return gain
```
`````

### Least Squares linear fit with NumPy

Define two arrays corresponding to measurements of two physical quantities $x$ and $y$ and let's assume that the uncertainty on $x$ is negligible with respect to the one on $y$.

It is possible to test the hypothesis of a linear relation between $y$ and $x$ by assuming $y = q + mx$, calculating the

$$
\chi^2 = \sum_{i=1}^N \left( \frac{y_i - q - mx_i}{\sigma_y}\right)^2
$$ 

and solving the system of linear equations defined by

$$
\begin{align*}
\frac{\partial\chi^2}{\partial m} &= 0\\ 
\frac{\partial\chi^2}{\partial q} &= 0
\end{align*}
$$

that can be written in matrix form as

$$
\begin{pmatrix}
N & \sum_{i=1}^Nx_i\\
\sum_{i=1}^Nx_i & \sum_{i=1}^Nx_i^2
\end{pmatrix}
\begin{pmatrix}
q\\
m
\end{pmatrix}=
\begin{pmatrix}
\sum_{i=1}^Ny_i\\
\sum_{i=1}^Nx_iy_i
\end{pmatrix}.
$$

Therefore, if the 2x2 matrix is invertible, the solution of the system of linear equations is

$$
\begin{pmatrix}
q\\
m
\end{pmatrix}=
\begin{pmatrix}
N & \sum_{i=1}^Nx_i\\
\sum_{i=1}^Nx_i & \sum_{i=1}^Nx_i^2
\end{pmatrix}^{-1}
\begin{pmatrix}
\sum_{i=1}^Ny_i\\
\sum_{i=1}^Nx_iy_i
\end{pmatrix}.
$$

Write a script to linearly fit a set of *n* data points using this technique.

### Linear fit comparison

Add the function used to perform the linear fit using NumPy and the matrices to a module and write a script that loads this function and the one defined in the previous lesson to compare the fit results on the same dataset.