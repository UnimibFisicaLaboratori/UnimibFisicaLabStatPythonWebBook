# Some python insight: classes, `lambda` functions, functional programming

## Object-Oriented programming in python

  * Basic python data types, like integers and float,
    may be used to **build more sophisticated mathematical objects**,
    such as complex numbers, fractions, matrices
  * Such high-level objects do have **their own behaviours and rules**:
    how to perform sums, multiplications, subtractions, *et cetera*
  * **A python ```class```** is a way to build high-level objects
    putting together the variables that define them
    and the functions that determine their behaviour

### The logic elements needed for a class

  * For such a construct to work, **some elements are necessary**: 
  ```{list-table} Necessary elements for a class
  :header-rows: 0
  :name: tab_necessary_class_elements
  * - **data members**
    - all the variables that compose the high-level object
  * - **constructor**
    - the function which builds each high-level object when initialized
  * - **methods**
    - the functions that operate on the object variables to implement its high-level behaviour
  ``` 
  <!-- | | |
  | ------------ | --------- |
  | **data members** | all the variables that compose the high-level object |
  | **constructor**  | the function which builds each high-level object when initialized |
  | **methods**      | the functions that operate on the object variables to implement its high-level behaviour | -->

### A class for handling fractions

  * All these components need to be **encased in a structure**,
    which is called ```class```
  * The following example shows a **simple implementation of a class**
    that may be used to handle numerical fractions (of integers) as high-level objecs:
    ```py
    from math import gcd
    class Fraction :
        '''
        # a simple class implementing a high-level object
        # to handle fractions and their operations
        '''

        def __init__ (self, numerator, denominator) :
            '''
            the constructor: initialises all the variables needed
            for the high-level object functioning
            '''
            if denominator == 0 :
              raise ValueError ('Denominator cannot be zero')
            if type(numerator) != int:
              raise TypeError ('Numerator must be an integer')
            if not isinstance(denominator, int ): # alternative way to check the type
              raise TypeError ('Denominator must be an integer')
            
            # this allows to avoid calculating the LCM in the sum and subtraction
            common_divisor = gcd (numerator, denominator) # greatest common divisor 
            self.numerator = numerator // common_divisor
            self.denominator = denominator // common_divisor
            
        def print (self) :
            '''
            prints the value of the fraction on screen
            '''
            print (str (self.numerator) + '/' + str (self.denominator))
    ```
    `````{tip}
    When user input is not valid for a function/class, it is useful to **raise** an [*exception*](https://docs.python.org/3/library/exceptions.html)
    ```py
    raise ValueError ('Denominator cannot be zero')
    ```
    This will stop the execution of the program and print the error message without exiting the python session.
    `````

### Using the class

  * The ```__init__``` function, called **constructor**, is necessary and operates all the necessary actions
    to **initialize a new high-level object of the type ```Fraction```**
  * The ```print``` function is a **method** of the class
    and is one of the operations one might want to do with a high-level object,
    ```py
    frac1 = Fraction (3, 4)
    frac1.print ()
    ```
  * The **```dot``` operator** allows to call class functions and access data members 
    for a high-level object
```{note}
The **keyword ```self```** identifies the high-level object.
  * A high-level object always is an **implicit argument of class functions**,
    and is therefore always present as fist argument of all class methods
  * The class **variabiles**, which characterise the high-level object, are identified
    with the preamble ```self.```
```

### Function overloading

  * Since the ```Fraction``` class describes the field of the rational numbers,
    **usual operations** like the sum, subtraction, multiplication, division 
    among fractions may be performed with specific rules
  * The python syntax allows to **define the behaviour of the usual symbols (`+`, `-`, `*`, `/`)**
    for the high-level objects built with the ```Fraction``` class
  * This property is called **overloading**
  ```py
    def __add__ (self, other) :
        '''
        implements the addition of two fractions.
        This function will be callable with the + symbol
        '''
        new_numerator = self.numerator * other.denominator + other.numerator * self.denominator
        new_denominator = self.denominator * other.denominator
        return Fraction (new_numerator, new_denominator)
    
    def __sub__ (self, other) : 
        # the - operator ...
    
    def __mul__ (self, other) :
        # the * operator ...
    
    def __truediv__ (self, other) :
        # the / operator ...
  ```

## Anonymous functions: `lambda`

  * The usual functional definition syntax **cannot be used within other instructions**:
    a function shall be defined before being used
    ```py
    def square (a):
        return a**2
    # ...
    print (square (number))
    ```
  * The `lambda` keyword allows to **define functions directly where they may be used**:   
    ```py
    print ((lambda x : x**2)(number))
    ``` 
  * The result of a `lambda` function definition may also be assigned to a variable, 
    since a function is a python object as well:
    ```py
    func = lambda x : x**2
    print (func (number))
    ``` 

## Functional programming

  * When dealing with lists and other containers,
    python offers ways of **acting on the whole collection of variables**
    automatically building optimized loops

### `map`

  * The built-in `map` function **applies a passed-in function to all elements of a list**:
    ```py
    lista = list (range (-5, 5))
    squared = list (map (square, lista))
    ```
    * in this case, `squared` is a new list containing the square of the elements of `lista`
  * **`lambda` functions may be used** with `map` for a more compact expression:
    ```py
    squared = list (map (lambda x : x**2, lista))
    ```

### `filter`

  * The built-in `filter` function **applies a passed-in function to all elements of a list and returns a list with the items for which the function is `True`**:
    ```py
    lista = list (filter (lambda x: x % 2 == 0, range(-5, 5)))
    ```


