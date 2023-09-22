# Exercises for Lecture 7

## Exercise 7.1

Generate a sample of pseudo-random numbers 
distributed according to an exponential density distribution
with a characteristic time t<sub>0</sub> of 5 seconds.
  * Visualize the distribution of the obtained sample
    in a histogram using the inverse function method.
  * Write all functions responsible for random number generation
    in a library, implemented in separate files from the main program.

## Exercise 7.2

Use the result from the first exercise to simulate a countng experiment
with Poisson characteristics:
  * Choose a characteristic time t<sub>0</sub> for a radioactive decay process;
  * Choose a measurement time t<sub>M</sub> for the counting window;
  * In a loop, simulate N pseudo-experiments of counting, where,
    for each of them, a sequence of random events is generated
    with an intertime characteristic of Poisson phenomena,
    until the total time elapsed is greater than the measurement time,
    counting the number of generated events that fall within the interval.
  * Fill a histogram with the simulated counts for each experiment.

## Exercise 7.3

Use the source code written in the previous exercise
to add to the library developed for exercise 1 a function
that generates random numbers
according to the Poisson distribution,
with the mean expected events as an input parameter.
  * Rewrite the previous exercise using this function,
    also drawing the probability density histogram.
  * Calculate the sample statistics (mean, variance, skewness, kurtosis)
    from the input list using a library.
  * Use the generated sample to test the functionality of the library.

## Exercise 7.4

  * Use the result from the previous exercise
    to calculate the statistics of a Poisson distribution
    varying the mean, from 1 to 250 (how should you sample the interval?).
  * Plot the obtained behavior of skewness and kurtosis as function of the Poisson mean.
