# Exercises for Lecture 2

## Exercise 2.1

  * Create one-dimensional NumPy arrays using different generation techniques

## Exercise 2.2

  * Create a one-dimentional NumPy array containing a sequence of integer numbers from 1 to 100
  * Starting from this, create a one-dimensional NumPy array
    containing in each entry the sum of integer numbers from 1 until the index of that entry

## Exercise 2.3

  * Create a one-dimensional array containing the sequence of the first 50 even natural numbers
  * Create a one-dimensional array containing the sequence of the first 50 odd natural numbers
  * Create a one-dimensional array containing the element-wise sum of the previous two arrays

## Exercise 2.4

Inside a Python program, the current time may be obtained with the `time` library:
```py
import time
time_snapshot = time.time ()
print (time_snapshot)
```
  * Compare the time performances of element-wise operations performed between two lists
    with respect to the same operation performed in compact form between two NumPy arrays
  * After which size the differences start being significant?  

## Exercise 2.5

  * After finding how the `numpy.sort` function works, 
    write a Python library containing a function that determines the median of an array.
  * Write a main program that tests the performance of the developed function.

## Exercise 2.6 

  * Given an array of numbers, write a Python library containing a function 
    which determines the the value below which lies the 25% of the values,
    and the one above which lies the 25% of the the values
  * Generalise the function to the case where the percentage of tails is set as input value

## Exercise 2.7

Write a Python library containing functions to perform the following operations
for NumPy 1D arrays:
  * Calculate the mean of its elements
  * Calculate the variance of its elements
  * Calculate the standard deviation of its elements
  * Calculate the standard deviation from the mean of its elements

## Exercise 2.8

Write a program that draws the basic trigonometric functions over a meaningful domain,
using NumPy universal functions
  * Show that the sin and cosin functions differ by a phase
  * Show that the terms *A* and *B* in the equation $f(x) = \sin (x-A) + B$ represent
    horizontal and vertical translations of the functional form, respectively
  * Show that the terms *C* and *D* in the equation $f(x) = D \cos (Cx)$ represent
    horizontal and vertical dilations of the functional form, respectivey

<!-- ## Exercise 2.X

Using NumPy ndarrays,
implement a program that calculates Lorentz boosts for four-vectors
to change the coordinates of a physical system.
 -->