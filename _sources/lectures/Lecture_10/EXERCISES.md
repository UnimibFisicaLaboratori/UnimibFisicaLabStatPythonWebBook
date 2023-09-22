# Exercises for Lecture 10

## Exercise 10.1

Write a library of functions to determine the parameter &tau; of an exponential distribution
from a list of numbers filled with pseudo-random numbers
distributed according to an exponential probability density distribution.
  * Compare the result obtained with the mean of the numbers saved in the list.
  * How does the result depend on the initial interval passed to the ```sezione_aurea_max_LL``` function?

## Exercise 10.2

 * Plot the profile of the likelihood function and the point identified as its maximum.

## Exercise 10.3

 * Modify the ```sezione_aurea_max_LL``` function,
   adding the printing of the interval endpoint values at each iteration,
   to observe the narrowing of the interval during program execution.

## Exercise 10.4

* Modify the ```loglikelihood``` function to calculate the logarithm of the product
   of the values of the probability density function, rather than the sum of individual logarithms.
   How does the algorithm's behavior change?

## Exercise 10.5

Graphically show that as the available sample size increases,
the profile of the logarithm of the likelihood function becomes narrower.
  * To simplify visualization, use the logarithm of the ratio
    between the likelihood function and its maximum value:
  
  $LLR\:(\theta) = \log \left( \dfrac{\mathcal{L}(\theta)}{\mathcal{L}(\hat{\theta})} \right)$

## Exercise 10.6

Use the bisection method to find the two points
*&tau; - &sigma;<sub>&tau;</sub>* and *&tau; + &sigma;<sub>&tau;</sub>*
related to Exercise 1.
  * Plot the log-likelihood profile, the estimator values, and the confidence interval
    along with the horizontal segment used for its determination.

## Exercise 10.7

Using the toy experiments technique,
plot the probability distribution of the &tau; estimator.
  * Overlay the generated histogram with the plot of the estimator and the confidence interval
    found in the previous exercise.
  * Compare the value of *&sigma;<sub>&tau;</sub>* obtained in the previous exercise
    with the one calculated from the distribution of the numbers saved in the list.

## Exercise 10.8

In the asymptotic regime,
the distribution of the differences *(&tau; - &tau;<sub>true</sub>) / &sigma;<sub>&tau;</sub>* 
follows a Normal distribution.
  * Use the toy experiments method to fill the histogram of the differences,
    given a number of events per toy experiment.
  * Calculate the mean and sigma of the distribution of differences,
    and plot their values as a function of the number of events available for estimation,
    showing the trend on a graph with the number of events available on the horizontal axis
    and the parameter value on the vertical axis.
