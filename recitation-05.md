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
|    100 |               0.115 |                0.105 |
|    200 |               0.211 |                0.300 |
|    500 |               0.782 |                0.713 |
|   1000 |               1.653 |                1.526 |
|   2000 |               3.271 |                4.183 |
|   5000 |              14.784 |               10.531 |
|  10000 |              20.004 |               19.404 |
|  20000 |              50.088 |               43.820 |
|  50000 |             139.596 |              128.965 |
| 100000 |             379.270 |              332.804 |

            O(n) = nlogn              O(n) = nlogn

this shows that that the big O time complexity of both of them is the same, and the run time of both functions is very similar, with light differnces due to the randomness of the lists

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
              O(n) = n^2            O(n) = nlogn
              
this shows that that the big O time complexity of fixed is bigger than that of random, and fixed too longer to run than random



**1c)**

Python uses a sorting algorithm called [*Timsort*](https://en.wikipedia.org/wiki/Timsort), designed by Tim Peters. Compare the fastest of your sorting implementations to the Python
sorting function `sorted`, conducting the tests in 1b above. 

Shuffled:
|      n |   qsort-fixed-pivot |   qsort-random-pivot |   tim_sort |
|--------|---------------------|----------------------|------------|
|    100 |               0.115 |                0.105 |      0.008 |
|    200 |               0.211 |                0.300 |      0.015 |
|    500 |               0.782 |                0.713 |      0.046 |
|   1000 |               1.653 |                1.526 |      0.082 |
|   2000 |               3.271 |                4.183 |      0.238 |
|   5000 |              14.784 |               10.531 |      0.510 |
|  10000 |              20.004 |               19.404 |      1.179 |
|  20000 |              50.088 |               43.820 |      2.495 |
|  50000 |             139.596 |              128.965 |      8.071 |
| 100000 |             379.270 |              332.804 |     17.607 |
                                                        O(n) = nlogn

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
                                                          O(n) = n

The big O time complexity of tim sort when non shuffled is much faster than when shuffled, which is reflected in the non shuffled program takign much less time to compleate than the shuffled one.