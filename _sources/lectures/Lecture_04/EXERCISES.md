# Exercises for Lecture 5

## Exercise 5.1

Write a function that implements the linear congruential generator for pseudo-random numbers,
using these parameters:
``` 
M = 2147483647
A = 214013
C = 2531011
```

## Exercise 5.2

Implement the generator in the form of an object,
which contains a method for generating a random number
and a method for setting the generation ```seed```,
using an appropriate variable of the class
to store this information.
  * How should the ```seed``` change
    every time a new random number is generated?

## Exercise 5.3

Show that initializing the seed of a pseudo-random integer generator
is equivalent to looking into a sequence of pseudo-random numbers
at any point.

## Exercise 5.4

Implement a pseudo-random number generator according to a uniform distribution
between two arbitrary endpoints.
  * Use the ```matplotlib``` library to visualize the distribution
    of the generated numbers.

## Exercise 5.5

Implement a pseudo-random number generator that uses the try-and-catch method
to generate pseudo-random numbers according to an arbitrary probability distribution.
  * Take the probability density function (pdf) as an input parameter
    for generating random numbers.
  * Use the ```matplotlib``` library to visualize the distribution
    of the generated numbers.

## Exercise 5.6

Implement a pseudo-random number generator that uses the inverse function method
to generate events distributed according to an exponential probability distribution.
  * Use the ```matplotlib``` library to visualize the distribution
    of the generated numbers.

## Exercise 5.7

Implement a pseudo-random number generator that uses the central limit theorem method
to generate events distributed according to a Gaussian probability distribution.
  * How can you obtain a normal distribution,
    i.e., a Gaussian distribution centered at zero with unit variance?
  * Visually verify that as the number of events increases,
    the similarity between the obtained distribution and the Gaussian functional form increases,
    both graphically and by using the moments of the distributions
    calculated on the generated event sample.

## Exercise 5.8

Building upon the work done during Lecture 3,
implement an object named ```stats```,
which calculates the statistics associated with a sample of numbers
stored in a Python list.
  * What different design options are possible for this object?
  * What variables need to be added to the class to ensure its functionality?
  * What values should these variables have during initialization?

## Exercise 5.9

Test the ```stats``` object with each of the implemented generation algorithms.
In particular, then:
  * Verify that the value of the variance for the uniform distribution corresponds to expectations
    (what is the uncertainty associated with the obtained number?)
  * Verify that the value of the variance obtained using the central limit theorem technique
    corresponds to the expected one.