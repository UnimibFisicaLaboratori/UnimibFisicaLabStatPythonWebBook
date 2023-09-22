# Finding Zeros and Extrema

## Finding the Zeros of a Function

  * Numerical techniques exist to **find the zeros** of a function.
  ```{admonition} Simple Assumptions
  :class: important
  * Function *g(x)* is **continuous and defined on a compact connected interval** *[x<sub>0</sub>, x<sub>1</sub>]*
  * At the interval boundaries, the function values **have opposite signs**
  * The function has **a single zero** within the interval
  ```

![Function with Zero](../../figs/funzione_con_zero.png)

### Bisection Method

* The program doesn't see the function as a whole,
  so the only way it can determine where the position of a zero
  is to **estimate the function at specific points**
* Given the initial assumptions,
  the zero of the function is certainly located between two points
  where the function **changes sign** between them
* The bisection technique **iteratively narrows down this interval**
  until it becomes smaller than a fixed resolution value
  ![Bisection](../../figs/bisezione.png)

### Implementation of the Bisection Algorithm

* At each iteration,
  the **midpoint of the interval** containing the zero is calculated,
  and it's determined whether the zero lies to its right or to its left
  ```py
  def bisezione (
      g,              # funzione di cui trovare lo zero
      xMin,           # minimo dell'intervallo          
      xMax,           # massimo dell'intervallo         
      prec = 0.0001): # precisione della funzione        
      '''
      Funzione che calcola zeri
      con il metodo della bisezione
      '''
      xAve = xMin 
      while ((xMax - xMin) > prec) :
          xAve = 0.5 * (xMax + xMin) 
          if (g (xAve) * g (xMin) > 0.): xMin = xAve 
          else                         : xMax = xAve 
      return xAve 
    ```

### Recursive Implementation of the Bisection Algorithm

* The bisection algorithm repeatedly performs the **same operation**
  recursively
* This behavior can also be implemented in ```python```,
  by writing a **recursive function** that calls itself:
  ```py
  def bisezione_ricorsiva (
      g,              # funzione di cui trovare lo zero  
      xMin,           # minimo dell'intervallo            
      xMax,           # massimo dell'intervallo          
      prec = 0.0001): # precisione della funzione        
      '''
      Funzione che calcola zeri
      con il metodo della bisezione ricorsivo
      '''
      xAve = 0.5 * (xMax + xMin)
      if ((xMax - xMin) < prec): return xAve ;
      if (g (xAve) * g (xMin) > 0.): return bisezione_ricorsiva (g, xAve, xMax, prec) ;
      else                         : return bisezione_ricorsiva (g, xMin, xAve, prec) ;
    ```

```{admonition} Attention
:class: warning
In every recursive function, there must be **two logical elements**:
* The **call to the function** itself
* The **exit condition** from the sequence of self-calls
  ```

## Finding Extremes: The Golden Ratio Method

```{admonition} Simple Assumptions
:class: important
* Function *g(x)* **continuously defined on a compact and connected interval** *[x<sub>0</sub>, x<sub>1</sub>]*
* The function has **a single extremum** within the interval
  ```

![Function with Minimum](../../figs/funzione_con_minimo.png)

* In this case as well, the process proceeds step by step,
  **narrowing the interval at each iteration** that contains the extremum
  until it becomes smaller than a predetermined precision value.

### Restriction Criterion

* To find the minimum of a function, enough points are needed to **understand its slope**
  in different regions of the interval.
  Hence, four points are sought for, which determine three intervals.
* The interval is narrowed by **eliminating the segment where the minimum is certainly not located**.
  ![Golden Section Slope](../../figs/sezione_aurea_pendenza.png)
* The following iteration narrows down to $[x_3,x_1]$ if $g(x_3) > g(x_2)$,
  to $[x_0, x_2]$ otherwise.

### Optimization of Point Selection

* To optimize the calculation, the points $x_2, x_3$ are chosen in a way that one of them can be
  **used in the subsequent iteration**, ensuring the same division ratio of the interval.
  ![Golden Ratio Point Selection](../../figs/sezione_aurea_r.png)
* For this to be possible, the following condition must hold:
  ![Golden Section Formula](../../figs/sezione_aurea_formula.png)
* Thus, **the iterative process narrows down** around the extremum of the function:
  ![Golden Section Iteration](../../figs/sezione_aurea.png)

## Putting Everything Together

* There are **many techniques** for finding zeros and extrema of functions,
  which are often the core of data analysis software.
* A collection of algorithms can be found in the volume **[numerical recipes](http://numerical.recipes/)**
* In addition to the local problem of performing operations under good regularity conditions,
  generic algorithms must also find a way to
  **reduce a general problem to simple cases**.
  * For instance, in the case of finding minima,
    algorithms must avoid finding local minima
    and not identifying the **global minimum** of a function.
* The functionality of an algorithm critically depends on the **dimension
  of the function definition space**.

:::{note}
  * The examples for the lecture may be found [here](EXAMPLES.rst)
  * The exercises for the lecture may be found [here](EXERCISES.md)
:::
