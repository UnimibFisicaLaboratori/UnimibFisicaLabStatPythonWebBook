# Notable Python Libraries

## NumPy

 * [NumPy](https://numpy.org) is the fundamental package for scientific computing in Python.
 * It provides a **multidimensional array object (`numpy.ndarray`)**, 
    various derived objects such as masked arrays and matrices,
    and an assortment of routines for fast operations on arrays.
 * To start using NumPy, simply import the library, usually with the abbreviation `np`:
   ```python
   import numpy as np
   ```

### Creating NumPy arrays

 * A `numpy.ndarray` is a **mutable** type.
 * The **creation** of a `numpy.ndarray` can be done in several different ways.
   * From a list:
     ```py
     a_list = [1, 2, 3,4]
     an_array = np.array (a_list)
     ```
     * **N.B.**: NumPy array types, while being named `ndarray`, are called with `numpy.array()`
   * Generating a collection of `N` zeroes:
     ```py
     an_array = np.zeros (N)
     ```
   * Generating a collection of `N` empty elements 
     (faster than the previous two, but no certainty on the array content is given):
     ```py
     an_array = np.empty (N)
     ```
   * Generating a range of integer elements
     ```py
     first = 1
     last = 11
     step = 2
     an_array = np.arange (first, last, step)
     ```
   * Generating values that are spaced linearly in a specified interval
     ```py
     number = 5
     an_array = np.linspace (first, last, number)
     ```

   ```{note}
   One main difference between the `ndarray` and Python `list` is that `ndarray` has **fixed size after declaration**
   It does not mean that the addition of elements is forbidden, 
   but it does technically require the creation of a new array and the destruction of the starting one.
   Therefore, given the memory management operations involved when adding a new element to a `ndarray`, 
   it is best to create the `ndarray` just before using it and fill a Python `list` if loops are involved 
   (see the example {ref}`examples:numpy:ndarray`).
   ```

### Array operations

 * Operations between arrays may be **written in compact form**, 
   making them clearer in writing and
   achieving a much faster execution,
   thanks to the use of optimised internal routines
 * the element-wise multiplication **performed with lists** requires a loop:   
   ```py
   list_a = list (range (10000))
   list_b = list (range (10000))
   list_prod = [list_a[i] * list_b[i] for i in range (len (list_a))]
   ```
 * the element-wise multiplication **performed with arrays** has a more compact form:   
   ```py
   array_a = np.array (list_a)
   array_b = np.array (list_b)
   array_prod = array_a * array_b
   ```
<!-- example {ref}`examples:numpy:ndarray_operations` -->

### Cumulative operations on arrays

 * The NumPy library contains functions that perform operations with the whole array:
 * The function `sum` adds all the values present in the array
 * The function `cumsum` calculates for each element the sum of all the elements preceeding it
 * The function `prod` multiplies all the values present in the array
 * The function `cumprod` calculates for each element the product of all the elements preceeding it

### Creating multi-dimensional arrays

 * A `ndarray` may have **more than one dimension** (usually called *axes*):
   ```python
   >>> multiD_array = np.array ([[1,2,3],[4,5,6]])
   >>> multiD_array
   array([[1, 2, 3],
          [4, 5, 6]])
   >>> multiD_array.shape
   (2, 3)
   ```
   * the `shape` of an array shows its **internal structure**, 
     in this case composed of two rows and three columns
 * The functions `zeros` and `ones` may be used also 
   to **create multi-dimensional objects**:
   ```py
   an_array = np.ones ((3,2))
   ```
    * this instruction will create an array with three rows and two columns

   ```{note}
   Accessing the array elements with `A[1,2]` is faster than `A[1][2]` 
   since the latter involves the creation in memory of another array.
   ```

### NumPy universal functions

 * Universal functions implement in a compact form operations on arrays,
   making it such that a **function may be called on an entire array**
   and act on its elements
 * Several **unviversal functions exist** (the full list may be found [here](https://numpy.org/doc/stable/reference/ufuncs.html#available-ufuncs),
   including 
   mathematical operations (e.g. `add`, `subtract`)
   and fundamental functions

## MatPlotLib

  * A widely used **library for visualisation** is [MatPlotLib](https://matplotlib.org/),
    which may be used to draw functions and histograms.
  * The first Python object that will be used in the course as a starting point
    is the [```matplotlib.pyplot```](https://matplotlib.org/stable/api/pyplot_summary.html) one, 
    which usually gets imported at the script beginning:
    ```py
    import matplotlib.pyplot as plt
    ```
  * When using the library,
    **two types of objects** will usually by created and handled:
    * [```matplotlib.axes```](https://matplotlib.org/stable/api/axes_api.html): 
      used for the plotting of the actual content of the figure
    * [```matplotlib.figure```](https://matplotlib.org/stable/api/figure_api.html): 
      used for axes creation and figure appearence
  * The creation of an empty image starts from the ```matplotlib.pyplot``` object:
    ```py
    fig, ax = plt.subplots (nrows = 1, ncols = 1)
    ```
    where ```fig``` and ```ax``` are the usual names given 
    to the ```matplotlib.figure``` and ```matplotlib.axes```
    objects that have been created.
    * The arguments of the ```subplots``` method indicate the **number of sub-plots**
      that will be present in the image,
      listed in rows and columns.
    * In case more than one sub-plot is present, 
      **the variable ```ax``` will be a container**: 
      a single list if ```nrows = 1``` or ```ncols = 1```, 
      a list of lists otherwise.
  * Once an image is created,
    it needs to be **visualised** on the screen with the call to the ```show``` function,
    **or saved** on disk with the call to the ```savefig``` function 
    of the object ```matplotlib.pyplot```:
    ```py
    plt.savefig ('example_01.png')
    plt.show ()
    ```

## Drawing functions

  * functions of the form *y = f(x)* are drawn as a **broken line joining a set of coordinates**:
    ```py
    # preparing the set of points to be drawn 
    x_coord = np.linspace (0, 2 * np.pi, 10_000)
    y_coord_1 = np.sin (x_coord)
    ```
    * the number of points, in this case ```10000```, sets the **smoothness of the drawing**
    * the variable ```y_coord_1``` is a **```numpy``` container**, 
      as it's the result of the action of a ```numpy``` function (hence vectorialized) to a ```numpy``` container
    * ```x_coord``` or ```y_coord_1``` may not be a ```numpy``` array,
      or the function to be plotted is not vectorialized; 
      in this case,
      their filling will have to be done, if needed, with loops
  * coordinates are then **drawn on an axis**:
    ```py
    ax.plot (x_coord, y_coord_1, label='sin (x)')
    ax.set_title ('Comparing trigonometric functions', size=14)
    ax.set_xlabel ('x')
    ax.set_ylabel ('y')
    ax.legend ()
    ```
    * some **information is added** to the plot: the general title of the graph,
      the title of the two axes,
      and the legend of the plot.
    * The **legend** uses the labels associated to a drawing as an argument to the ```ax.plot``` function
  * **several functions or objects may be drawn on the same axis**
    and the ```matplotlib``` libraries will take care of adapting the axis ranges accordingly:
    ```py
    def func (x) :
        return np.cos (x - np.pi / 2.)

    y_coord_2 = np.arange (0., x_coord.size)
    y_coord_2 = func (x_coord)
    ax.plot (x_coord, y_coord_2, linestyle = 'dashed', label='cos (x) - pi/2')
    ```
<!--     for i in range (x_coord.size):
        y_coord_2[i] = func (x_coord[i])
 -->


:::{note}
  <!-- * The examples for the lecture may be found [here](EXAMPLES.rst) -->
  * The exercises for the lecture may be found [here](EXERCISES.md)
:::
