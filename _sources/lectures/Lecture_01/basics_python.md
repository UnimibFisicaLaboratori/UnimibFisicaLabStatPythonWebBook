# Basics of Python Programming

```{note}
List of subjects that might be useful in the future
  * list comprehensions
  * use of asterisk in passing variables (DONE)
  * exercises on kernel reloading when discussing notebooks (in the likelihood lecture?):
    * when an imported library is changed, need to reload
    * when a variable changes name, the old one remains active until reloading
    * rerun from start
```

## Objectives of the laboratory

  * Use a programming language and libraries available to **perform probability and statistics exercises** 
  * The choice of the programming language and statistics tools is **instrumental**
  * Every physicist should be **ready to change tools when needed**
    * learning new tools quickly
    * understanding how libraries work and whether they are suited for the problem to be tackled

## The [Python](https://www.python.org) programming language

<!-- ![PythonLogo](https://www.python.org/static/community_logos/python-logo-master-v3-TM.png) -->

<!-- ```{epigraph}
Python is an interpreted, object-oriented, high-level programming language with dynamic semantics. Its high-level built in data structures, combined with dynamic typing and dynamic binding, make it very attractive for Rapid Application Development, as well as for use as a scripting or glue language to connect existing components together. Python's simple, easy to learn syntax emphasizes readability and therefore reduces the cost of program maintenance. Python supports modules and packages, which encourages program modularity and code reuse. The Python interpreter and the extensive standard library are available in source or binary form without charge for all major platforms, and can be freely distributed.

-- from [www.python.org](https://www.python.org/doc/essays/blurb/)
```
 -->
  * **high-level**: it has a strong abstraction from the details of the computer. 
    It uses natural language elements, is easy to use and automates significant areas of computing systems 
    like memory management
  * **interpreted**: no program compilation action is needed by the user
  * **object-oriented**: organised around data, or objects, rather than functions and logic
  * **dynamic semantics**: its variables are dynamic and can change memory size and values during execution

### Typical uses

  * **Rapid Application Development**: a fast development and testing of ideas and prototype, 
    with less emphasis on planning;
    ```{warning}
    Python may not be the best programming language for a big and complex fail-proof application
    ```
  * **scripting**: writing small programs or scripts that control other programs
  * **glue language**: it is able to deal with libraries compiled with different languages and use them

### Main advantages

  * simple, easy to learn **syntax**, **readable-friendly**, with a steep learning curve
    It also provide a **standard library** of functions developed by the community 
    that covers almost all the needs of a normal user.
  * **support of modules and packages** written by other users and available to the community

### The Python Prompt

  * Once the Python program is executed from the program shell, 
    a command line is prompted on the terminal, the **so-called "Python prompt"**
  * Simple Python commands, sets of instructions or programs
    may be **directly typed there and executed**
    ```bash
    $ python
    Python 3.11.4 (main, Jun 20 2023, 16:59:59) [Clang 14.0.3 (clang-1403.0.22.14.1)] on darwin
    Type "help", "copyright", "credits" or "license" for more information.
    >>> 
    ```
<!-- fragment -->
  * The Python prompt is recognised by the `>>>` symbol and is **ready to receive commands**:
    ```python
    >>> 2+2
    4
    >>> 7*6/2
    21.0
    ```
    ```{note}
    The Python prompt may be **useful for quick checks**,
    but it does not replace actual programming.
    ```

### Programming in Python

  * A **computer program** is a set of instructions meant to guide the computer hardware
    in doing calculations, by using the computing processing unit (CPU)
    and the memory
  * A program is structured accoding to **rules dictated by the programming language**
  * In this brief introduction we will see the **main elements** to be used to build a Python program
    ```{list-table} Main Python programming elements
    :name: tab_python_syntax_elements
    * - **variables** 
      - write information into the computer memory and read it back 
    * - **functions**
      - groups of sequences of elementary instructions into a repeatable block
    * - **control sequences**
      - fundamental structures to handle sequences of elementary instructions (choices, iterations) 
    * - **modules**
      - libraries of fully-developed tools to implement specific behaviours 
    ```

## Variables

  * Information needs to be **handled according to its nature**, 
    in terms of occupied memory space and elementary operations
    ```{list-table} Logical Operators in Python
    :header-rows: 1
    :name: tab_python_types

    * - variable 
      - use   
    * - integer
      - `a = 1`
    * - floating point
      - `a = 1.0`
    * - complex
      - `a = 3 + 2j`
    * - boolean
      - `a=True`
    * - string
      - `a='filename.txt'`
    * - `None`
      - object is not defined
    ```

    ```{note}
    For a detailed list and description of built-in Python types see the 
    [official Python documentation](https://docs.python.org/3/library/stdtypes.html#)
    ```

  * Python is **not statically typed**:
    variables do not need to be declared before use, nor their type to be declared 
    `````{admonition} Tip
    :class: tip
    Use the [`type`](https://docs.python.org/3/library/functions.html#type) built-in function to know what is the current type of the object
    `````

### Numbers

  * **Integers** can take up to any positive or negative number in an unlimited range 
    (subject to the available virtual memory).
  * **Floating point** numbers are implemented as the same as `double` in C 
    ($1.7\times 10^{\pm308}$ with 15 digits).
  * **Complex numbers** have a real and imaginary part, which are a floating point number each.

    ```python
    >>> a = 4
    >>> type(a)
    <class 'int'>
    >>> b = 5.
    >>> type(b)
    <class 'float'>
    >>> c = 4 + 5j
    >>> type(c)
    <class 'complex'>
    ```

    ```{note}
    A number is automatically interpreted as imaginary by adding `j` (or `J`) to its value
    ```

  * If needed, the functions (called constructors) `int()`, `float()`, and `complex()` can be used 
    to **generate numbers of specific type**.

    ```python
    >>> a = complex (4)
    >>> type (a)
    <class 'complex'>
    >>> a
    (4+0j)
    >>> b = int (5.) # this call operates a type conversion (casting)
    >>> type (b)
    <class 'int'>
    >>> b
    5
    ```

 * The **real and imaginary part of a complex number** `z` can be accessed 
   by calling `z.real` and `z.imag` and they are returned as `float`

    ```python
    >>> z = complex(4,5)
    >>> z.real
    4.0
    >>> z.imag
    5.0
    >>> type(z.imag)
    <class 'float'>
    ```

### Boolean

  * **Booleans** are variables that can only take the value `True` or `False`
  * They support the **logical operators** `or`, `and` and `not`
    ```{list-table} Logical Operators in Python
    :header-rows: 1
    :name: tab_logical_operators
    * - Operation 
      - Result
    * - `x or y` 
      - if `x` is true, then `x`, else `y`
    * - `x and y`
      - if `x` is false, then `x`, else `y`
    * - `not x`
      - if `x` is false, then `True`, else `False`
    ```
  * the **result of a comparison** is a boolean
    ```python
    >>> 5>3
    True
    >>> 5*3>20
    False
    ```
    ```{list-table} Comparison Operators in Python
    :header-rows: 1
    :name: tab_comparison_operators
    * - Operation
      - Meaning
    * - `<`
      - strictly less than
    * - `<=`
      - less than or equal
    * - `>`
      - strictly greater than
    * - `>=`
      - greater than or equal
    * - `==`
      - equal
    * - `!=`
      - not equal
    * - `is`
      - object identity
    * - `is not`
      - negated object identity
    ```
    * For a full list of comparison operators, see {numref}`tab_comparison_operators`
  * **Different operations**, when not ordered with parentheses,
    **have different priority** as determined by the programming language
  * The **comparison** has lower priority than mathematical operations, 
    but higher than the logical ones
    ```python
    >>> 5*3>20 and 5>3
    False
    ```
    * Finally, `not` has a lower priority than non-Boolean operators, 
      so `not a == b` is interpreted as `not (a == b)`, and `a == not b` is a syntax error.

### Strings

  * **Textual data** in Python is handled with `str` objects, or *strings*.
    Strings are **written** in a variety of ways:
    * single quotes: `'allows embedded "double" quotes'`
    * double quotes: `"allows embedded 'single' quotes"`
    * triple quotes: `'''Three single quotes'''`, `"""Three double quotes"""`
    Triple quote strings may span multiple lines - all associated whitespaces will be included in the string literal.

    ```python
    >>> 'my single quote string'
    'my single quote string'
    >>> "my double quote string"
    'my double quote string'
    >>> """my triple quote string"""
    'my triple quote string'
    >>> """my triple quote string
    ... spanning multiple
    ... lines"""
    'my triple quote string\nspanning multiple\nlines'
    ```

    ```{note}
    A string is a list of characters, when spanning multiple lines the corresponding Unicode character `\n`
    for the new line is added to the list
    ```

### `None`

  * It represents a **null value, or no value at all**
  * **Different from all other types** (e.g. it's not `True`, nor `False`)
  * It indicates that **the object is not defined** and therefore occupies no space in memory.
    Any operation between an object that is `None` and another one returns into an error.
    ```python
    >>> a = None
    >>> type(a)
    <class 'NoneType'>
    >>> a*2
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    TypeError: unsupported operand type(s) for *: 'NoneType' and 'int'
    ```

## Object containers

  * Single variables may be **collected in containers**
  * Containers are **by themselves variable types**
    * Therefore, **containers of containers** may be built
  * **Different types** of containers exist, depending on the **behaviour needed**
    when handling the collection of variables

    ```{list-table} Python built-in containers
    :header-rows: 1
    :name: tab_python_containers

    * - container 
      - use 
      - example  
    * - [list](https://docs.python.org/3/tutorial/datastructures.html#more-on-lists)
      - ordered, changeable, allows duplicates, items are indexed
      - `[1, 2, 3]`
    * - [tuple](https://docs.python.org/3/tutorial/datastructures.html#tuples-and-sequences)
      - ordered, unchangeable, allows duplicates, items are indexed
      - `(1, 2, 3)`
    * - [set](https://docs.python.org/3/tutorial/datastructures.html#sets)
      - unordered, unchangeable, does not allow duplicate values
      - `{1, 2, 3}`
    * - [dictionary](https://docs.python.org/3/tutorial/datastructures.html#dictionaries)
      - items are presented in `key:value` pairs, ordered (in the `key`), changeable, 
        does not allow duplicates (of elements with the same `key`)
      - `{1:'a', 2:'b', 3:'c'}`  
    ```

### Lists

  * Mutable **sequences of objects**, 
    typically used to store collections of homogeneous objects, 
    but Python allows also inhomogeneous lists.
  * Can be **constructed in several ways**:
    * Using a pair of square brackets to create an empty list: `[]`
    * Using square brackets, separating items with commas: `[a]`, `[a, b, c]`
    * Using the type constructor: `list()` or `list(iterable)`    
    ```python
    >>> test_list = [1,2,3]
    >>> type(test_list)
    <class 'list'>
    >>> test_list = [1, float (2), complex (3)]
    >>> test_list
    [1, 2.0, (3+0j)]
    >>> type (test_list)
    <class 'list'>
    ```
  * **Elements may be added** with the `append` function:
    ```python
    >>> test_list = [1,2,3]
    >>> print (test_list)
    [1, 2, 3]
    >>> test_list.append (7)
    >>> print (test_list)
    [1, 2, 3, 7]
    ```
    * the dot (`.`) between `test_list` and the function `append`
      indicates that **the function has to act on that specific list**
  * The **order of the items** in the list is the same given in the assignation.
  * There are various **operations possible** on the lists, as detailed in {numref}`tab_list_operations`

    ```{list-table} List operations
    :header-rows: 1
    :name: tab_list_operations
    * - Operation
      - Result
    * - `x in test_list`
      - `True` if an item of `test_list` is equal to `x`, else `False`
    * - `x not in test_list`
      - `False` if an item of `test_list` is equal to `x`, else `True`
    * - `test_list_1 + test_list_2`
      - returns a new list which is the concatenation of `test_list_1` and `test_list_2`
    * - `test_list * n` or `n * test_list`
      - equivalent to adding `test_list` to itself `n` times
    * - `test_list[i]`
      - returns the i-th item of `test_list`, starting the counting from 0
    * - `test_list[i:j]`
      - returns a sub-list, called *slice*, containing the elements of `test_list` from `i` to `j`
    * - `test_list[i:j:k]`
      - returns a sub-list containing the elements of `test_list` from `i` to `j` with step `k`
    * - `len(test_list)`
      - returns number of elements contained in `test_list`
    * - `min(test_list)`
      - returns smallest item of `test_list`
    * - `max(test_list)`
      - returns the largest item of `s`
    * - `test_list.index(x)`
      - returns the index of the first occurrence of `x` in `test_list`
    * - `test_list.index(x, i, j)`
      - returns the index of the first occurrence of `x` in `test_list`, at or after index `i` and before index `j`
    * - `test_list.count(x)`
      - counts the total number of occurrences of `x` in `test_list`
    ```

    ```python
    >>> a = [1,2,3]
    >>> print (a[1])
    2
    >>> print (a[1:3])
    [2, 3]
    >>> b = [4,5,6]
    >>> c = a+b
    >>> print (c)
    [1, 2, 3, 4, 5, 6]
    >>> print (c[1:4:2])
    [2, 4]
    >>> print (len(c))
    6
    >>> print (min(c))
    1
    >>> print (max(c))
    6
    >>> c = c*4
    >>> print (c)
    [1, 2, 3, 4, 5, 6, 1, 2, 3, 4, 5, 6, 1, 2, 3, 4, 5, 6, 1, 2, 3, 4, 5, 6]
    >>> print (len(c))
    24
    >>> print (c.index(4))
    3
    >>> d += [4,3,4]
    >>> print (d)
    [2, 1, 4, 3, 6, 5, 4, 3, 4]
    >>> print (d.count(4))
    3
    ```

    `````{admonition} Tip
    :class: tip
    A special list is given by the type `range`, 
    which represents an immutable sequence of numbers commonly used for looping a specific number of times in `for` loops
    ```python
    >>> list(range(4))
    [0, 1, 2, 3]
    >>> list(range(1,8,2))
    [1, 3, 5, 7]
    ```
    `````

    ```{note}
    Since strings are substantially lists of characters, all the list operations can be performed on them.
    ```

### Tuples

  * They are **defined by a set of objects separated by commas**
  * When printed they are **shown within parentheses**
    ```python
    >>> test_tuple = 1, 2, 3, 'this', 'is', 'a', 'tuple'
    >>> print (test_tuple)
    (1, 2, 3, 'this', 'is', 'a', 'tuple')
    ```
  * Their elements can be **accessed via indexing**
    ```python
    >>> test_tuple[4]
    ```
  * or via **unpacking**
    ```python
    >>> a1, a2, a3, b1, b2, b3, b4 = test_tuple
    >>> print( a1, a2, a3, b1, b2, b3, b4 )
    1 2 3 this is a tuple
    ```
    `````{note}
    Unpacking can also be performed by means of the `*` operator
    ```python
    >>> print( *test_tuple )
    1 2 3 this is a tuple
    ```
    `````
  * Cannot be modified after creation, 
    since they are an [**immutable**](https://docs.python.org/3/glossary.html#term-immutable) type
    ```python
    >>> t[4]= 0
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    TypeError: 'tuple' object does not support item assignment
    ```

### Dictionaries

  * Define an **associative array** object. 
  * Contain a **set of `key: value` pairs**, with the requirement that the keys are unique within each dictionary
  * Are indexed by *keys*, which can be any immutable type (often *strings* or *numbers*)
  * A **pair of braces** creates an empty dictionary: `{}`. 
  * Placing a comma-separated list of `key: value` pairs within the braces adds initial `key: value` pairs to the dictionary; 
    this is also the way dictionaries are written on output.
    ```python
    >>> test_dict = { 'a': [1,2,3], 'b': 'my string', 1: 0}
    >>> print (test_dict)
    {'a': [1, 2, 3], 'b': 'my string', 1: 0}
    >>> print (test_dict['a'])
    [1, 2, 3]
    >>> test_dict['test'] = 1+3J
    >>> print (test_dict)
    {'a': [1, 2, 3], 'b': 'my string', 1: 0, 'test': (1+3j)}
    ```
  * Iterations on a dictionary may be done in a similar way to the lists:
    ```py
    >>> for key in test_dict: print (key, test_dict[key]) 
    ```
  * alternative ways do exist
    ```py
    >>> for key in test_dict.keys (): print (key) 
    >>> for value in test_dict.values (): print (value) 
    >>> for key, value in test_dict.items (): print (key, value) 
    ```

## Python memory handling

  * When creating a new variable or assigning a value to it,
    **three steps** comceptually take place:
    1. **Create in memory an object** to contain the value assigned
    2. **Create the Python variable** (if not existing)
    3. **Link the variable** to the new object
  * Threfore, **all variables are references** to the actual objects saved in memory
  * Variables are classified in **two main categories**:
    * **immutable objects** cannot changed in place
    * **mutable objects** may be changed in place
    ```{list-table} Python mutable and immutable variables
    :header-rows: 1
    :name: tab_python_mut_immut
    * - mutable
      - immutable 
    * - lists, sets, user-defined classes, dictionaries
      - int, float, bool, string, tuple
    ``` 
    `````{note}
    When a new value is assigned to an immutable variable,
    the variable itself changes the object it points to
    `````
  * When **a mutable variable is passed to a function**, 
    any modifications done inside the function propagate outside the function,
    to the scope where the function is called from
  * When **an immutable variable is passed to a function**,   
    modifications do not affect the variable outside the function

## Python scripts

  * A Python script is a **sequence of instructions**
    written in a text file
    to be **executed by the python interpreter**
  * Let the script be saved in a file called `script_01.py`, 
    and have the form:  
    ```py
    print ('hello world')
    ```
  * The following **shell command** will ask the Python interpreter
    to open the script, execute it
    and end the execution:
    ```bash
    $ python3 script_01.py
    ```

### Interactive running

  * It is sometimes useful to **run a script in interactive mode**, 
    meaning that Python will not exit after the execution of the program.
    For example, in the case you want to inspect the final values of the variables:
    ```bash
    $ python3  -i my_first_script.py
    25
    >>> 
    ```

## Functions

  * Functions are a **set of instructions grouped which may be called together**,
    that produce a given output or action 
  * They are **identified with a name and set of inputs**

### an example: the `print` function

  * The `print` function is used to **print the value of a variable on the screen**
    at a certain point during the execution of the program
  * It takes as **input** a variable to be printed
    and **visualises its value** on the screen  
    ```python
    >>> a = 5
    >>> print (a)
    5
    ```
  * It can also be used to print messages or any other value, 
    since it interprets its argument as an input variable
    ```python
    >>> print('this is a message')
    this is a message
    >>> print(42)
    42
    ```

### another example: user input

  * The program can be instructed to **accept an input from the user** 
    and store it into a variable by means of the `input ()` function.
  * `input` takes a string as argument, 
    representing the message that will be printed on screen to instruct the user.

    ```python
    >>> a = input('insert a number: ')
    insert a number: 2
    >>> print (a)
    '2'
    ```

  * By default **`input` returns a string**, 
    and casting should be used to interpret it as a different variable

    ```python
    >>> a = int (input ('insert a number:'))
    ```

### User-defined functions

  * The keyword `def` introduces a **function definition**
    that is used to define new functions implemented by users
  * It must be followed by the **function name**, 
    **its arguments** within parentheses and a colon (`:`)

    ```python
    def squared (x) :
      return x*x
    ```
  * The commands inside the function need to be **written 
    displaced towards the right** by a fixed shift
  * This operation, called **indentation**,
    is the way chosen in Python programming to define a **scope**,
    which is a set of instructions at the same logical level
    ```{warning}
    - Indentation shall be **generous** (2 spaces at least)
    - Intentation shall be done **always with the same character** 
      (TABs and spaces are *not* the same thing)
    ```
  * The function may or may not **return something** where it has been called
  * In case it does, it may return **a single object or a sequence of them**
    (interpreted as a *tuple*)
    ```python
    >>> def first_three_powers (x) :
    ...   return x, x*x, x*x*x
    ... 
    >>> first_three_powers (2)
    (2, 4, 8)
    ```

### Functions with arbitrary number of arguments

  * It is possible to define a function with an **arbitrary number of arguments** 
    by using the `*args` and `**kwargs` syntax.
  * In this case, **the `*` operator is used to unpack a list or a tuple 
    into a function call**, 
    so that each element of the list is passed as a different argument to the function.
  * Similarly, 
    **the `**` operator can be used to pass keyword arguments in the form of a dictionary**.

    ```python
    def my_function(*args, **kwargs):
       print(args)
       print(kwargs)
    
    my_function( (1,2,3), a = 1, b = 'wow', c= (4,5,6))
    ((1, 2, 3),)
    {'a': 1, 'b': 'wow', 'c': (4, 5, 6)}
    ```

    ```{warning}
    Defining functions with an arbitrary number of arguments is a powerful feature, 
    but it should be used with care. 
    All the operations that are performed on the arguments inside the function body 
    should be valid for all the possible types of arguments that the function can receive.
    ```

### Functions in python scripts

  * When a program gets some structure,
    it's wise to **write it within a script**,
    so that it can be carefully edited before execution
  * For example, 
    **several functions may be defined** in the same script  
  * To let the Python interpreter know what to do when a script is called,
    the **main sequence of instructions** follows the statement `if __name__ == "__main__":
`
    ```py
    def squared (x) :
      return x*x

    if __name__ == "__main__":
      number = float (input ('insert a number:'))
      print ('the square of ' + str (number) + ' is: ' + str (squared (number)))
    ```  

    `````{tip}
    When writing a script, it is advisable to **define a `main ()` function**
    that will be executed when the script is called
    ```python
    def main () :
      <your code statements here>
      return

    #-------------------------------

    if __name__ == "__main__":
      main ()
    ```
    `````

### Documenting function behaviour

  * The first statement of the function body can be a string literal, 
    in which case it will be interpreted as **the documentation of the function**
    that can be accessed by the built-in function `help`.
    ```python
    >>> def squared (x):
    ...   '''calculates the square of a number'''
    ...   return x*x
    ... 
    >>> help (squared)
    ```
  * The code above will open a new page with the documentation of the function:

    ```python
    Help on function squared in module __main__:

    squared(x)
        calculates the square of a number
    (END)
    ```

    * To exit, press `q`.

    `````{admonition} Documentation styles
    :class: note
    Since in the Python language the information is inplicit
    (as the type of the variables),
    **special care has to be put in documenting the source code**:
    explain what is the purpose of the function in a concise way 
    and describe the arguments with their type, as well the expected result type.

    ```python
    def squared(x):
      """calculates the square of a number
      
      Args:
        x (float): a number
      
      Returns:
        (float): the square of x
      """
      return x*x
    ```

    The output of `help(squared)` is in this case much more helpful.

    ```python
    Help on function squared in module __main__:

    squared(x)
        calculates the square of a number
        
        Args:
          x (float): a number
        
        Returns:
          (float): the square of x
    ```
    `````

### Variables inside functions

  * Variables defined in the scope of a function, called **local**, 
    are not visible outside it unless they are declared as `global`.

    ```python
    >>> def test(x):
    ...   y = 4
    ...   return x
    ... 
    >>> test(1)
    1
    >>> y
    Traceback (most recent call last):
      File "<stdin>", line 1, in <module>
    NameError: name 'y' is not defined
    >>> def test(x):
    ...   global y
    ...   y = 4
    ...   return x
    ... 
    >>> test(1)
    1
    >>> y
    >>> 4
    ```

  * On the other side, 
    a function **may access and manipulate objects defined outside its scope** 
    and not passed as arguments
    ```python
    >>> a = 8
    >>> def test(x):
    ...   return a*x
    ... 
    >>> test(2)
    16
    ```
  * Whenever a variable is defined within the scope of the function 
    with the same name as a variable outside its scope, 
    **it behaves as a new local variable**.

    ```python
    >>> a = 8
    >>> def test(x):
    ...   a = 4
    ...   return a*x
    ... 
    >>> test(1)
    4
    >>> a
    >>> 8
    ```

## Control Flow Tools

### Checking conditions: `if` and `else` statements

  * It is quite common in programming to let the program execute a set of commands 
    **only when a condition is met**.
    This is possible in Python with the `if` statement.
    ```python
    >>> a = 3
    >>> if a > 0 : 
    ...   print('a is positive')
    ... 
    a is positive
    >>> 
    ```
    * As in the case of functions,
      instructions following an `if` statement
      **shall be indented**
  * If different commands should be executed **depending on the value the condition**,
    the `else` statement comes to support.

    ```python
    >>> a = -3
    >>> if a > 0: 
    ...   print('a is positive')
    ... else: 
    ...   print('a is negative')
    ... 
    a is negative
    ```
  * **Multiple cases** are covered by using the `elif` statement.

    ```python
    >>> a = 0
    >>> if a > 0: 
    ...   print('a is positive')
    ... elif a < 0: 
    ...   print('a is negative')
    ... else: 
    ...   print('a is zero')
    ... 
    a is zero
    ```

### The `for` loop

  * **Repetitive operations** can be executed by means of the `for` and `while` loops.
  * The **`for` loop** executes the same set of instructions
    for all the elements of a list of objects
    ```python
    >>> for elem in [0,1,'a','abc',5.] :
    ...   print (elem)
    ... 
    0
    1
    a
    abc
    5.0
    ```
  * The variable `elem` can be used within the loop 
    and assumes, one by one,
    the **value of each element** present in the list
  * Loops **over integer indices** are usually performed using the `range` function:
    ```python
    for i in range (3):
      print ('iteration ' + str (i))
    ```
  * As in the case of functions,
    instructions following a `for` statement
    **shall be indented**
    * This allows, for example, to **uniquely identify scopes** in nested loops
    ```python
    for i in range (3):
      print ('before the internal loop in iteration ' + str (i))  
      for j in range (3):
        number = 3 * i + j
        print (number)
      print ('end of internal loop')  
    ```

### The `while` loop

  * The `while` loops execute a set of instructions 
    **as long as a condition is fulfilled**

    ```python
    >>> i = 3
    >>> while i > 0:
    ...   print(i)
    ...   i -= 1
    ... 
    3
    2
    1
    ```

### Exceptional loop interruction instructions

  * Sometimes it is useful to alter the behaviour of loops
    independently of the conditions present in the `for` or `while` statements
  * The `continue` instruction
    interrupts the execution of the instructions in the scope
    and **jumps to the following iteration**
  * The `break` instrution interrupts the execution of the iteration
    and exits the loop 

## Modules

  * Colletions of functions to be used in many programs
    may be collected in **libraries or modules**
    that can be imported in scripts

### An example: reading the command line

  * When a script is executed,
    it's **very practical to provide input information** in the same command line:
    ```bash
    $ python3 script_03.py 3
    the square of 3.0 is: 9.0
    ```
  * The *library* that is used to read the input line is called `sys`
    ```py
    import sys

    def squared (x) :
      return x*x

    if __name__ == "__main__":

      number = float (sys.argv[1])
      print ('the square power of ' + str (number) + ' is: ' + str (squared (number)))
    ```
    * The instruction `import` allows to **import the `sys` library** ready for use
    * The **`sys.argv` list** contains all the words written after `python3`

### User-defined libraries

  * A library is a **text file containing a collection of functions**,
    usually placed in the same directory of the scripts which use it

    ```{eval-rst}
    .. literalinclude:: ./examples/script_04.py
       :language: python
    ```

  * where in this case [`operations`](./examples/operations.py) is

    ```py
    def squared (x) :
      """calculates the square of a number
      
      Args:
        x (float): a number
      
      Returns:
        (float): the square of x
      """
      return x * x
    ```

    ```{eval-rst}
    .. literalinclude:: ./examples/script_04.py
       :language: python
    ```

    `````{note}
    Adding the following term to the library
    allows to **run the library as a script** for testing purposes
    ```python
    if __name__ == "__main__":

      number = 3.
      print ('the square power of ' + str (number) + ' is: ' + str (squared (number)))  
    ```
    `````


:::{note}
  * The examples for the lecture may be found [here](EXAMPLES.rst)
  * The exercises for the lecture may be found [here](EXERCISES.md)
:::

<!-- A notebook with the examples proposed in this lecture can be found [here](../examples/basics_python_examples.ipynb) -->


