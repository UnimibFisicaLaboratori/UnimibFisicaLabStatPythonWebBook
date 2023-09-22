# Exercises for Lecture 8

## Exercise 8.1

Write a program that, given a number *N_max*,
generates *N_toys* toy experiments,
each containing a sample of *N_max* events following a chosen distribution,
and calculates their mean.

## Exercise 8.2

Add to the previous program a histogram
that visualizes the distribution of means across the toy experiments.

## Exercise 8.3

Use the ```stats``` class developed during the previous Lectures
to compare the standard deviation of the mean calculated for each individual toy
with the standard deviation of the sample of means.

## Exercise 8.4

Use two scatter plots to compare the evolution
of the standard deviation of the mean calculated for each individual toy
with the standard deviation of the sample of means
as the number of events generated in a single toy experiment varies.

## Exercise 8.5

Implement the hit-or-miss integration method
with the example function *f(x) = sin(x)*.
  * Write the algorithm that calculates the integral as function external to the ```main``` program,
    ensuring it takes as input parameters the limits along the *x* and *y* axis,
    as well as the number of pseudo-random points to generate.
  * Make sure the algorithm returns a container with two elements:
    the first element is the value of the integral,
    the second is its uncertainty.

## Exercise 8.6

Insert the calculation of the integral from the previous exercise into a loop that,
as the number *N* of generated points varies, displays the value of the integral
and its uncertainty.
  * Use a scatter plot to visualize the trends of the integral value
    and its uncertainty as *N* varies on a logarithmic scale.

## Exercise 8.7

Implement the crude-MC integration method
with the example function *f(x) = sin(x)*.
  * Write the algorithm that calculates the integral as a function external to the ```main``` program,
    ensuring it takes as input parameters the limits along the *x* axis
    and the number of pseudo-random points to generate.
  * Make sure the algorithm returns a container with two elements:
    the first element is the value of the integral,
    the second is its uncertainty.

## Exercise 8.8

Insert the calculation of the integral from the previous exercise into a loop that,
as the number *N* of generated points varies, displays the value of the integral
and its uncertainty.
  * Plot the trends of the integral value and its uncertainty
    as *N* varies on a logarithmic scale.
  * Overlay this behavior with the one obtained from completing Exercise 8.6.

## Exercise 8.9

Use the hit-or-miss method to estimate the integral underlying
a Gaussian probability distribution with *&mu;=0* and *&sigma;=1*
within a generic interval *[a,b]*.
  * Calculate the integral contained within the intervals *[-k&sigma;, k&sigma;]*
    as *k* varies from *1* to *5*.
