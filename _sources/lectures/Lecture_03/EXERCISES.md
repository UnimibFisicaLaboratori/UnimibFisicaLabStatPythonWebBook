# Exercises for Lecture 3

## Exercise 3.1

  * Create a one-dimensional histogram filled with 5 values and save the histogram image to a `png` file

## Exercise 3.2

Read the text file [eventi_unif.txt](https://raw.githubusercontent.com/UnimibFisicaLaboratori/UnimibFisicaLabStatPython/main/book/lectures/Lecture_03/exercises/eventi_unif.txt?token=GHSAT0AAAAAACIWS3PPQPW7EDJ35WURR4NMZJL6ZNA)

  * Print the first 10 positive elements to the screen.
  * Count the number of events contained in the file.
  * Determine the minimum and maximum values among the numbers saved in the file.

```{admonition} Instructions to download the file
:class: tip
  To access the RAW version of the file, click on the ```Raw``` button at the top-right. 
  To download it, one can use two methods:
  1. Open the link and use 'Save as' from your browser.
  2. Use the command `wget <link>` in the directory where the file has to be saved (e.g.: `$ wget rawFileAddress`)
```

## Exercise 3.3

Read the text file [```eventi_gauss.txt```](https://github.com/UnimibFisicaLaboratori/UnimibFisicaLabStatPython/blob/main/book/lectures/Lecture_03/exercises/eventi_gauss.txt):
  * Fill a histogram with the first N numbers contained in the file,
    where N is a command-line parameter during program execution.
  * Choose the histogram's definition range and its bin number
    based on the numbers to be represented.

## Exercise 3.4

  * Display the distributions of events from the two files of the previous exercises, overlaid,
    finding the best visualization for the comparison between the two histograms.

## Exercise 3.5

Read the text file [```eventi_unif.txt```](https://raw.githubusercontent.com/UnimibFisicaLaboratori/UnimibFisicaLabStatPython/main/book/lectures/Lecture_03/exercises/eventi_unif.txt?token=GHSAT0AAAAAACIWS3POIJNNHAQOSCNMXEN2ZJL63FQ):
  * Calculate the mean of the numbers in the text file.
  * Calculate the variance of the numbers in the text file.
  * Calculate the standard deviation of the numbers in the text file.
  * Calculate the standard deviation from the mean of the numbers in the text file.

## Exercise 3.6

Write a ```python``` library which,
given the name of a text file containing a sample of events as input,
is able to read the sample and save it in a numpy array,
then calculate its mean, variance, standard deviation, standard deviation from the mean,
display the sample in a histogram
with an appropriately chosen definition range and bin number.
Write a test program for the created library.

## Exercise 3.7

Write a Python program to draw a Gaussian distribution and its cumulative function

## Exercise 3.8

Write a Python program to draw an exponential distribution and its cumulative function

## Exercise 3.9

Use the Python `scipy.stat.norm` object to determine the area of a normal distribution
of its tails outside the range included within an interval of 1, 2, 3, 4, and 5 standard deviations around its mean

## Exercise 3.10

Write a Python program to draw a binomial distribution and its cumulative function

## Exercise 3.11

Write a Python program to draw a Poisson distribution for several values of its mean, overlapped

## Exercise 3.12

Write a Python program to draw a Poisson distribution.
Show, by using the third and fourth central momenta calculations available in the `scipy.stat` library,
that the momenta of a Poisson distribution asymptotically tend to the ones of a Gaussian.

## Exercise 3.13

What is the probability that ten measurements of the same quantity
expected to be Gaussian fall within an interval of 1 standard deviation width around the mean?

## Exercise 3.14

What is the probability that ten measurements of the same counting experiment
expected to be Poisson distributed are all larger than the expected average number 
of events?
