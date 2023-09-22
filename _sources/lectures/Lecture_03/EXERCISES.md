# Exercises for Lecture 3

## Exercise 3.1

  * Create a one-dimensional histogram filled with 5 values and save the histogram image to a `png` file

## Exercise 3.2

Read the text file [eventi_unif.txt](https://github.com/UnimibFisicaLaboratori/UnimibFisicaLabStatPython/blob/main/book/lectures/Lecture_03/exercises/eventi_unif.txt)

  * Print the first 10 positive elements to the screen.
  * Count the number of events contained in the file.
  * Determine the minimum and maximum values among the numbers saved in the file.

```{admonition} Instructions to download the file
:class: tip
  To access the RAW version of the file, click on the ```Raw``` button at the top-right. 
  TO download it, tou can use two methods:
  1. Open the link and use 'Save as' from your browser.
  2. Use the command `wget <link>` in the directory where you want to save it (e.g.: `$ wget rawFileAddress`)
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

Read the text file [```eventi_unif.txt```](https://raw.githubusercontent.com/UnimibFisicaLaboratori/UnimibFisicaLab2/master/Lezione_03/programmi/eventi_unif.txt):
  * Calculate the mean of the numbers in the text file.
  * Calculate the variance of the numbers in the text file.
  * Calculate the standard deviation of the numbers in the text file.
  * Calculate the standard deviation from the mean of the numbers in the text file.

## Exercise 3.6

Write a ```python``` class in the form of a library which,
given the name of a text file containing a sample of events as input,
is able to store the sample internally,
calculate its mean, variance, standard deviation, standard deviation from the mean,
display the sample in a histogram
with an appropriately chosen definition range and bin number.
Write a test program for the created class.
