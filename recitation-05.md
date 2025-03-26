# CMPS 2200 Recitation 5

In this recitation, we'll look at randomness in computation.

**To make grading easier, please place all written solutions directly in `answers.md`, rather than scanning in handwritten work or editing this file.**

All coding portions should go in `main.py` as usual.


## Determinism versus Randomization in Quicksort

In lecture we saw that adding a random choice of pivot reduced the
probability of worst-case behavior for any given input in
selection. Let's look at how pivot choices affect Quicksort. For this
question, refer to the code in `main.py` 

**1a)**

Complete the implementations of `qsort` and `compare_sort` stubs. Feel
free to take from code given in the lectures to  help you perform list
partitioning. Note that the pivot choice function is input to `qsort`,
so you will have to curry `qsort` to test different methods of
choosing pivots. Implement variants of `qsort` that correspond to
selecting the first element of the input list as the pivot, and to
selecting a random pivot.
.  
.  
.  
.  


**1b)**

Compare running times using `compare-sort` between variants of
Quicksort and the
provided implementation of selection sort (`ssort`). Perform two
different comparisons: a comparison between sorting methods using
random permutations of the specified sizes, and a comparison using
already sorted permutations. How do the running times compare to the
asymptotic bounds? How does changing the type of input list change the
relative performance of these algorithms? Note that you may have to
modify the list sizes based on your system memory; compare at least 10
different list sizes. The `print_results` function in `main.py` gives
a table of results, but feel free to use code from Lab 1 to plot
the results as well. 

Shuffled:
|      n |   qsort-fixed-pivot |   qsort-random-pivot |
|--------|---------------------|----------------------|
|    100 |               0.134 |                0.127 |      
|    200 |               0.346 |                0.267 |      
|    500 |               1.211 |                1.324 |      
|   1000 |               2.438 |                1.868 |      
|   2000 |               7.293 |                4.469 |      
|   5000 |              18.472 |               15.043 |      
|  10000 |              29.523 |               36.330 |
|  20000 |              70.176 |               53.940 |
|  50000 |             156.332 |              208.535 | 
| 100000 |             366.666 |              486.127 |

 Non Shuffled:
 |      n |   qsort-fixed-pivot |   qsort-random-pivot |
 |--------|---------------------|----------------------|
 |    100 |               0.224 |                0.198 |     
 |    200 |               2.398 |                0.254 |
 |    500 |               0.851 |                0.938 |
 |   1000 |               2.890 |                1.745 |
 |   2000 |               4.317 |                3.397 |
 |   5000 |              11.701 |               11.929 |      
 |  10000 |              23.429 |               23.446 |      
 |  20000 |              49.479 |               45.079 |      
 |  50000 |             143.209 |              144.322 |      
 | 100000 |             320.508 |              303.647 |      

**1c)**

Python uses a sorting algorithm called [*Timsort*](https://en.wikipedia.org/wiki/Timsort), designed by Tim Peters. Compare the fastest of your sorting implementations to the Python
sorting function `sorted`, conducting the tests in 1b above. 

Shuffled:
|      n |   qsort-fixed-pivot |   qsort-random-pivot |   tim_sort |
|--------|---------------------|----------------------|------------|
|    100 |               0.134 |                0.127 |      0.021 |
|    200 |               0.346 |                0.267 |      0.015 |
|    500 |               1.211 |                1.324 |      0.048 |
|   1000 |               2.438 |                1.868 |      0.087 |
|   2000 |               7.293 |                4.469 |      0.336 |
|   5000 |              18.472 |               15.043 |      0.640 |
|  10000 |              29.523 |               36.330 |      1.493 |
|  20000 |              70.176 |               53.940 |      3.270 |
|  50000 |             156.332 |              208.535 |     34.574 |
| 100000 |             366.666 |              486.127 |     32.216 |

Non Shuffled:
|      n |   qsort-fixed-pivot |   qsort-random-pivot |   tim_sort |
|--------|---------------------|----------------------|------------|
|    100 |               0.224 |                0.198 |      0.003 |
|    200 |               2.398 |                0.254 |      0.004 |
|    500 |               0.851 |                0.938 |      0.007 |
|   1000 |               2.890 |                1.745 |      0.012 |
|   2000 |               4.317 |                3.397 |      0.024 |
|   5000 |              11.701 |               11.929 |      0.056 |
|  10000 |              23.429 |               23.446 |      0.091 |
|  20000 |              49.479 |               45.079 |      0.108 |
|  50000 |             143.209 |              144.322 |      0.696 |
| 100000 |             320.508 |              303.647 |      1.049 |