# Least-Squares Fitting

## The method of Least Squares

  * The method of **least squares** is based on a principle independent
    of that of maximum likelihood
  * Parameters &theta; are chosen to make the **distance minimal**
    between the model and the data,
    according to a metric defined by the average standard deviation
    of the measurements with respect to the model

### An immediate example

  * To determine the mean $\mu$ of a set of measurements $x_i$,
    the following function can be minimized:

    $$
    Q^2 = \sum_{i=1}^N \left( \frac{x_i-\mu}{\sigma}\right)^2
    $$
<!-- ![Q_media](../../figs/Q_media_2.png) -->

### The $y=\phi(x)$ case

  * The same metric is often used
    for **data regression**, also known as *fitting*
  * Let *N* pairs of independent measurements be given in the form $(x_i,y_i)$,
    for which:
    * the uncertainty on the value $x_i$ is **negligible or zero**
    * **the uncertainty on the value $y_i$** is $\sigma_i$
  * Assume that the two variables $x_i$ and $y_i$
    are **related to each other through a function $\phi$** such that $y=\phi(x,\theta)$
  * The **function $Q^2(\theta)$** is defined as:

  $$
  Q^2(\theta) = \sum_{i=1}^N \left( \frac{y_i-\phi(x_i,\theta)}{\sigma_i}\right)^2
  $$

<!-- ![Q_funzione_2](../../figs/Q_funzione.png) -->

### Determination of the fit parameters $\theta$

  * In this case, the parameters $\theta$ ($\theta$ may be a vector)
    are determined by **finding the minimum of the function $Q^2(\theta)$**:

    $$
    \frac{\partial Q^2(\theta)}{\partial \theta_l} = 0
    $$
<!-- ![Q_funzione](../../figs/Q_derivata.png) -->
  * Various numerical techniques exist to find the minimum of the function

### Properties of the Least-Squares method

  * If the residuals $\epsilon_i$ of $y_i$ with respect to $\phi(x_i,\theta)$
    have a **zero mean and finite, constant variance**,
    that is, independent of $y$, 
    and $\phi(x_i,\theta)$ is linear in the $\theta)$ parameters,
    then
    * the least squares method is an **unbiased estimator** of the parameters $\theta$
    * and it has the **minimum variance** among all unbiased linear estimators (in $y$),
      regardless of the probability distribution of the residuals
  * If the residuals $\epsilon_i$ are distributed according to a Gaussian probability density distribution,
    the minimum of the function $Q^2(\theta)$
    is distributed according to a **$\chi^2$ distribution**
    with *N-k* degrees of freedom,
    * where *N* is the **number of pairs** $(x_i,y_i)$*
      and *k* is the **number of estimated parameters**

### Least-Squares for linear functions

  * In the case where the function *g(x)* is **linear in the parameters $\theta$**,
    the minimization equations can be solved analytically

    $$
    \phi(x,\theta) = \sum_{i=1}^{k}\theta_i h_i(x)
    $$

<!-- ![g_lineare](../../figs/phi_lineare.png) -->

  :::{note}
  * An example of a linear function is **the line
    $\phi(x,\theta) = \theta_1 + \theta_2 x$**:
    * $h_1(x) = 1$
    * $h_2(x) = x$
  * Another example of a linear function is **a parabola
    $\phi(x,\theta) = \theta_1 + \theta_2 x + \theta_3 x^2$**:
    * $h_1(x) = 1$
    * $h_2(x) = x$
    * $h_3(x) = x^2$
  :::


## A Regression exercise

  * Using pseudo-random number generation,
    it is possible to **simulate the collection of N independent measurements $(x_i,y_i)$**
    based on an initial model $y=\phi(x,\theta)$,
    for example:
    ```py
    epsilons = generate_TCL_ms (0., epsilon_sigma, 10)

    x_coord = np.arange (0, 10, 1)
    y_coord = np.zeros (10)
    for i in range (x_coord.size) :
        y_coord[i] = func (x_coord[i], m_true, q_true) + epsilons[i]
    ```
  * where pseudo-random number generation (```generate_TCL_ms```)
    is used to **find the values of the terms $\epsilon_i$**
  * the $\x_i$ points may also be generated is a pseudo-random manner

### Plotting the data

  * The ```iminuit``` library provides tools that **automatically apply
    the least squares method** to find the parameters
  * Pairs of measurements like those generated are usually represented
    in the form of scatter plots:
    ```py
    sigma_y = epsilon_sigma * np.ones (len (y_coord))
    fig, ax = plt.subplots ()
    ax.set_title ('linear model', size=14)
    ax.set_xlabel ('x')
    ax.set_ylabel ('y')
    ax.errorbar (x_coord, y_coord, xerr = 0.0, yerr = sigma_y, linestyle = 'None', marker = 'o') 
    ```
    * `sigma_y` is the **expected** uncertainty in this case

### Parameters determination

  * The **fit operation** is performed with the following instructions:
    ```py
    from iminuit import Minuit
    from iminuit.cost import LeastSquares

    # generate a least-squares cost function
    least_squares = LeastSquares (x_coord, y_coord, sigma_y, func)
    my_minuit = Minuit (least_squares, m = 0, q = 0)  # starting values for m and q
    my_minuit.migrad ()  # finds minimum of least_squares function
    my_minuit.hesse ()   # accurately computes uncertainties
    ```
    * the `least_squares` object contains **the cost function** that will be minimized
    * the `my_minuit` object will operate the actual minimization,
      **starting the search from the initial point** `m = 0, q = 0`
      in the parameter phase space
    * the `my_minuit.migrad ()` call **performs the minimization**
    * the `my_minuit.hesse ()` **evaluates parameter uncertainties**
      by computing an approximation of the parameter covariance matrix

## Analyzing the result of the regression

### Fit convergence

  * Whether the minimization **has been successful** can be inquired:
    ```py
      # global characteristics of the fit
    is_valid = my_minuit.valid
    print ('success of the fit: ', is_valid)
    ```
  * The value of **$Q^2$ and the number of degrees of freedom**
    may be obtained as well:
    ```py
    Q_squared = my_minuit.fval
    print ('value of the fit Q-squared', Q_squared)
    N_dof = my_minuit.ndof
    print ('value of the number of degrees of freedom', N_dof)
    ```  

### Fit quality

  * In case the probability density distribution of the individual $y_i$ follows a Gaussian
    probability density function, 
    the **$Q^2_{\text{min}}$ quantity follows the $\chi^2$ distribution** 
    with $N-k$ degrees of freedom, 
    where $N$ is the number of fitted bins and $k$ is the number of determined parameters
  * Under these conditions, 
    the **$\chi^2$ test** can be used to determine the goodness of the fit 
    by calculating the probability that the result could be worse than what was obtained, 
    integrating the $\chi^2(N-k)$ distribution from $Q^2_{\text{min}}$ to infinity. 
  * The values of $Q^2_{\text{min}}$ and the number of degrees of freedom 
    can be obtained from the `Minuit` variable as well:
    ```cpp
    print ('Value of Q2: ', my_minuit.fval)
    print ('Number of degrees of freedom: ', my_minuit.ndof)
    ```
  * The **p-value** associated to the fit result
    may be calculated from the cumulative distribution function
    of the $\chi{}^2$ probability density function:
    ```py
    from scipy.stats import chi2
    # ...
    print ('associated p-value: ', 1. - chi2.cdf (my_minuit.fval, df = my_minuit.ndof))
    ```

### Parameter values and uncertainty

  * The **fit results** are stored in the `my_minuit` oject:
    ```py
    for par, val, err in zip (my_minuit.parameters, my_minuit.values, my_minuit.errors) :
        print(f'{par} = {val:.3f} +/- {err:.3f}') # formatted output
        
    m_fit = my_minuit.values[0]
    q_fit = my_minuit.values[1]  
    ```
    * `my_minuit.parameters` contains the parameter names
    * `my_minuit.values` the parameter values
    * `my_minuit.errors` the parameter uncertainty

### Covariance matrix of the fit parameters

  * The covariance matrix of the resulting parameters **can be printed to the screen**:
    ```py
    print (my_minuit.covariance)
    ```
  * Its **individual values** can be accessed as well,
    either by numerical index,
    or by unsing parameter names:
    ```py
    print (my_minuit.covariance[0][1])
    print (my_minuit.covariance['m']['q'])    
    ```
  * The parameter **correlation matrix** is easily calculated from the covariance one:
    ```py
    print (my_minuit.covariance.correlation ())
    ```

### Quick inspection of the fit results

  * The **screen output** of the fit sumamrises all the information above,
    and may be displayed with the call:
    ```py
    display (my_minuit)
    ``` 

## Measurement uncertainties and the least-squares method

  * In the case where the random variables $\epsilon_i$ have a Gaussian probability density distribution,
    **the value of $Q^2$ associated with the fit
    follows a $\chi^2$ distribution**
    with a number of degrees of freedom equal
    to the degrees of freedom of the fit
     * the degrees of freedom of the fit is equal to the 
       **number of data points minus the number of estimated parameters**
  * This property of the least squares method allows, 
    assuming that the random variables $\epsilon_i$ are Gaussian,
    the estimation of uncertainties on the values $y_i$

:::{note}
  * The exercises for the lecture may be found [here](EXERCISES.md)
:::
