# Exercises for Lecture 12

## Exercise 12.1

Write a program that fits the events saved in the file
   [```dati.txt```](https://drive.google.com/file/d/19Csfi4zrSz0bLREXOaPaWicIUUmstHQz/view?usp=sharing).
  * Take care to determine the range and binning of the histogram used for the fit
    based on the events themselves,
    writing appropriate algorithms to determine the minimum and maximum of the sample
    and a reasonable estimate of the number of bins to use.
  * Determine the initial values of the fit parameters
    using the techniques described in the lesson.
  * Print the fit result on the screen.
  * Plot the histogram with the fitted model overlaid.
  * Which parameters are correlated, and which are anti-correlated with each other?

## Exercise 12.2

Generate a file ```dati_2.txt``` containing 10,000 events
distributed according to a Gaussian probability distribution.
  * Write a program that fits the events saved in the file ```dati_2.txt```
    using the binned and unbinned maximum likelihood methods,
    and compare the results of the two techniques.

## Exercise 12.3

Insert the source code of the previous exercise into a loop
that performs the comparison as the number of events considered for the fit varies,
from ```20``` to ```10000```, with a regular log-scale increment.
  * Use different plots
    to show the behavior of the parameters and their uncertainties
    as the number of events changes, for both types of estimators.
  * Add to the comparison the fit performed with the least squares method.
  * Which estimator is less biased at low statistics?

## Exercise 12.4

Starting from samples of pseudo-random numbers generated 
according to a Gaussian probability density function,
using the technique of the toy experiments
study the distribution of the minimum of the cost function
used by `iminuit` in Gaussian fits.
  * Does it match a $\chi^2$ distribution for any number of events,
    for the cases of maximum likelihood, extended maximum likelihood, and least squares?
