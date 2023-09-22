# Exercises for Lecture 9

## Exercise 9.1

Write a program that generates pseudo-random numbers
distributed according to an exponential function
and stores them in a list.

## Exercise 9.2

Add to the previous program the source code that fills a histogram
with the numbers present in the list where they have been transferred,
and displays the histogram on the screen.

## Exercise 9.3

Write a program
that plots the exponential probability distribution
with a fixed parameter *t<sub>0</sub>*.

## Exercise 9.4

Write a function ```likelihood``` that calculates the likelihood
as the parameter *t<sub>0</sub>* varies,
for a sample of pseudo-random events generated according to the instructions of Exercise 1.
  * How does the result depend on the number of events in the sample?

## Exercise 9.5

Write a function ```loglikelihood``` that calculates the logarithm of the likelihood
as the parameter *t<sub>0</sub>* varies,
for a sample of pseudo-random events generated according to the instructions of Exercise 1.
Remember that the logarithm of the likelihood is defined
only when the *likelihood* is strictly positive.

## Exercise 9.6

Study the behavior of the shape of the log-likelihood as a function of the number of events
comprising the generated sample.
