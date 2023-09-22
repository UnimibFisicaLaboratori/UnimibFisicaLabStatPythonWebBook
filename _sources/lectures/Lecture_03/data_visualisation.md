# Data Visualisation with Python

## MatPlotLib

  * A widely used **library for visualisation** is [MatPlotLib](https://matplotlib.org/),
    which may be used to draw functions and histograms.
  * The first Python object that will be used in the course as a starting point
    is the [```matplotlib.pyplot```](https://matplotlib.org/stable/api/pyplot_summary.html) one, 
    which usually gets imported at the script beginning:
    ```py
    import matplotlib.pyplot as plt
    ```
  * When using the library,
    **two types of objects** will usually by created and handled:
    * [```matplotlib.axes```](https://matplotlib.org/stable/api/axes_api.html): 
      used for the plotting of the actual content of the figure
    * [```matplotlib.figure```](https://matplotlib.org/stable/api/figure_api.html): 
      used for axes creation and figure appearence
  * The creation of an empty image starts from the ```matplotlib.pyplot``` object:
    ```py
    fig, ax = plt.subplots (nrows = 1, ncols = 1)
    ```
    where ```fig``` and ```ax``` are the usual names given 
    to the ```matplotlib.figure``` and ```matplotlib.axes```
    objects that have been created.
    * The arguments of the ```subplots``` method indicate the **number of sub-plots**
      that will be present in the image,
      listed in rows and columns.
    * In case more than one sub-plot is present, 
      **the variable ```ax``` will be a container**: 
      a single list if ```nrows = 1``` or ```ncols = 1```, 
      a list of lists otherwise.
  * Once an image is created,
    it needs to be **visualised** on the screen with the call to the ```show``` function,
    **or saved** on disk with the call to the ```savefig``` function 
    of the object ```matplotlib.pyplot```:
    ```py
    plt.savefig ('example_01.png')
    plt.show ()
    ```

## Drawing functions

  * functions of the form *y = f(x)* are drawn as a **broken line joining a set of coordinates**:
    ```py
    # preparing the set of points to be drawn 
    x_coord = np.linspace (0, 2 * np.pi, 10_000)
    y_coord_1 = np.sin (x_coord)
    ```
    * the number of points, in this case ```10000```, sets the **smoothness of the drawing**
    * the variable ```y_coord_1``` is a **```numpy``` container**, 
      as it's the result of the action of a ```numpy``` function (hence vectorialised) to a ```numpy``` container
    * ```x_coord``` and ```y_coord_1```; in this case,
      their filling will have to be done, if needed, with loops
  * coordinates are then **drawn on an axis**:
    ```py
    ax.plot (x_coord, y_coord_1, label='sin (x)')
    ax.set_title ('Comparing trigonometric functions', size=14)
    ax.set_xlabel ('x')
    ax.set_ylabel ('y')
    ax.legend ()
    ```
    * some **information is added** to the plot: the general title of the graph,
      the title of the two axes,
      and the legend of the plot.
    * The **legend** uses the labels associated to a drawing as an argument to the ```ax.plot``` function
  * **several functions or objects may be drawn on the same axis**
    and the ```matplotlib``` libraries will take care of adapting the axis ranges accordingly:
    ```py
    def func (x) :
        return np.cos (x - np.pi / 2.)

    y_coord_2 = np.arange (0., x_coord.size)
    for i in range (x_coord.size):
        y_coord_2[i] = func (x_coord[i])
    ax.plot (x_coord, y_coord_2, linestyle = 'dashed', label='cos (x) - pi/2')
    ```

## Reading and writing text files with Python

  * It is frequently useful to **save data on text files 
    and to be able to recover them** for a later use,
    either to avoid inserting them one by one during a script execution,
    or to have them saved in a separate place with respect to the script source code.

### Writing information on txt files

  * The **writing procedure** may be done in the following way:
    ```py
    with open ('sample.txt', 'w') as output_file :
        for item in sample:
            # write each item on a new line
            output_file.write (str (item) + '\n')
    ```
    * The ```sample``` variable is an existing collection of numbers
    * the printout adds a carriage return symbol ```\n```, 
      so to ensure that the numbers are saved in different lines

### Reading information from txt files

  * The **reading procedure** may be done in the following way:
    ```py
    with open (sys.argv[1]) as input_file:
    sample = [float (x) for x in input_file.readlines()]
    ```
    * The ```sample``` variabile gets created while reading the text file
    * The ```readlines ()``` function returns strings, 
      which need to be converted into floats for them to be used as sample elements

## Histograms

  * **Histograms** are a representation of differential distributions,
    constructed from a sample of numbers,
    which we call **events**
  * We start with **a sample of events _{x<sub>i</sub>}<sub>i=1,..,N</sub>_**
    * An example of a sample of events
      is **the set of measurements collected during an experiment**,
      or a **sequence of pseudo-random numbers**

### Histogram Bins

  * For a random variable of interest *x*, its interval of definition is divided
    into **adjacent and disjoint sub-intervals** delimited by *{x<sub>k</sub>}*
    * The *k*-th interval is bounded between x<sub>k</sub> and x<sub>k+1</sub>
    * Usually, these intervals are called **bins**
  * An histogram is the **collection of event counts that fall within each interval**
  ![istogramma](../../figs/histo_alone.png)
  * The visualization of a one-dimensional histogram typically shows:
    * On the **horizontal axis**, the interval of definition of the variable *x*
    * On the **vertical axis**, the counts corresponding to each bin
    * Above each bin, **a vertical bar** as high as the counts in the bin
 
### One-Dimensional Histograms and Probability Density Distributions

  * As the **bin size approaches infinitesimal**, an histogram becomes a continuous function
  ![histogram_pdf](../../figs/histo_and_pdf.png)
  * If the content of each bin is divided by the total number of events *N*,
    this function becomes normalized,
    thus an histogram **approximates a probability density distribution**

### Histogram building and representation in ```matplotlib```

  * Given a sample of numbers, its **visualisation in a histogram form** 
    may be obtained with the following instructions:
    ```py
    fig, ax = plt.subplots (nrows = 1, ncols = 1)
    ax.hist (sample,
             color = 'orange',
            )
    ```
    where the input ```sample``` is a collection of values
    * The *x* axis range and its division into bins is **automtically performed**
      by the ```hist``` function

### Histogram drawing options control

  * Very frequenly -- always in this course -- one wants to have
    **control over the *x* axis range and binning**,
    for a proper statistical use of the histogram
    and for comparisons across histograms.  
  * This may be achieved by **explicitly defining the bin boundaries**
    and providing them as input with the ```hist``` function:
    ```py
    bin_edges = np.linspace (xMin, xMax, N_bins)
    print ('length of the bin_edges container:', len (bin_edges))
    fig, ax = plt.subplots (nrows = 1, ncols = 1)
    ax.hist (sample,
             bins = bin_edges,
             color = 'orange',
            )
    ```

### The number of bins

  * Depending on the sample size, **the number of bins shall be adapted**:
    * on the one hand, **with more events it may be increased**, with very few events it has to remain small
      to gather at least some events per bin
    * on the other hand, **it's of no use that the size of each bin is much smaller** than the typical
      shape changes in the histogram
   ![histogram_binning](../../figs/compare_binnings.png)     
  * The choice of ```N_bins``` is therefore relevant for a proper representation: 
    a recipe frequently used is the so-called Sturges' rule:
    ```py
    from math import ceil
    def sturges (N_events) :
         return ceil (1 + 3.322 * np.log (N_events))
    ```
    which may be used as follows in the drawing instructions:
    ```py
    N_bins = sturges (len (sample))
    bin_edges = np.linspace (xMin, xMax, N_bins)
    ```

### Logarithmic scales

  * When the values in different bins change considerably,
    it can be convenient to **visualize histograms on a logarithmic scale**
    (along the horizontal or vertical axis),
    to improve the readability of the result
  * Being a different visualization of the same content,
    this operation is performed using a method of the ```axes``` object
    ```py
    ax.set_ylabel ('y')

    ```
      * Clearly, the zero of the logarithmic scale axis cannot appear in the images
   ![log_scale](../../figs/log_scale_example.png)     


## Calculate and draw sample moments

  * Given the sample,
    its **moments may be calculated** by replacing expectation values
    with sample averages, for example:
    $$
    E[x] = \int_{-\infty}^\infty x\:f(x)\:dx ~ \to ~ \sum^N_{i=1} x_i / N
    $$
  * The **corresponding ```python``` script** to implement this call is then:
    ```py
    return sum (sample) / len (sample)   
    ```
    * the ```python``` function ```sum``` calculates the sum of the ```sample``` elements
    * the ```python``` function ```len``` calculates its number of elements
  * once the average is known, its drawing may be added to a histogram:
    ```py
    ax.hist (sample,
             bins = bin_edges,
             color = 'orange',
            )
    vertical_limits = ax.get_ylim ()
    ax.plot ([sample_mean, sample_mean], vertical_limits, color = 'blue')
    ```
    to obtain the following visualisation
   ![mean_drawing](../../figs/histo_mean.png)   

:::{note}
  * The examples for the lecture may be found [here](EXAMPLES.rst)
  * The exercises for the lecture may be found [here](EXERCISES.md)
:::

