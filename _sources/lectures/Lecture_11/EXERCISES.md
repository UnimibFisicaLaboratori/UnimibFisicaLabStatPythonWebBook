# Exercises for Lecture 11

## Exercise 11.1

After defining, in a dedicated library,
a linear function $\phi(x, \theta)$ with two parameters $\theta$:
  * Write a program that generates a set of *10* pairs $(x_i, y_i)$
    such that the points $x_i$ are randomly distributed along the horizontal axis
    between 0 and 10, and the points $y_i$ are constructed using the formula $y_i = \phi(x_i, \theta) + \epsilon_i$.
  * Plot the obtained sample, including the expected error bars.

  `````{hint}
  :class: dropdown
  - Use this prototype for the function $\phi(x, \theta)$:
    ```python
    def phi (x, m, q) :
      """a linear function

      Args:
          x (float): the `x` value
          m (float): the slope
          q (float): the intercept
      """    
    ```
  - generate the $\epsilon_i$ values using the appropriate function from [myrand](myrand_library) if you did not write your own yet. Assume the same uncertainty for all points.
  - Use the [`matplotlib.pyplot.errorbar`](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.errorbar.html) function to plot the points with the error bars.
  `````

## Exercise 11.2

Use the ```iMinuit``` library to perform a fit on the simulated sample.
  * Check if the fit was successful.
  * Print the values of the determined parameters and their sigmas on the screen.

## Exercise 11.3

  * Calculate the value of $Q^2$ using the points and the fitted function
    obtained in the previous exercise.
  * Compare the value obtained with ```iminuit``` with the calculated one.
  * Print the value of the degrees of freedom of the fit.

## Exercise 11.4

Using the toy experiments technique,
generate 10,000 fit experiments with the model studied in the previous exercises
and fill a histogram with the obtained values of $Q^2$.
  * Compare the expected value of $Q^2$ obtained from the toy experiments
    with the degrees of freedom of the problem.

## Exercise 11.5

Modify the previous program by deliberately changing the experimental uncertainty
associated with the points $y_i$ in the sample and verify that it's possible to recover the 
uncertainty used in generating the points
through the expected value of the variable $Q^2$.

## Exercise 11.6

Add to Exercise 11.3 the screen printout of the entire covariance matrix
of the fit parameters.

## Exercise 11.7

Repeat the fitting exercise for a parabolic trend.
