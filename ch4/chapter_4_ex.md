Chapter_4
================

\#coding basics

``` r
1/200*30
```

    ## [1] 0.15

``` r
(59+73+2)/3
```

    ## [1] 44.66667

``` r
sin(pi/2)
```

    ## [1] 1

\#creating objects

``` r
x <- 3*4  #alt minus shortcut
x
```

    ## [1] 12

\#assignments

``` r
this_is_a_really_long_name <- 2.5
this_is_a_really_long_name
```

    ## [1] 2.5

``` r
this_is_a_really_long_name <- 3.5
this_is_a_really_long_name
```

    ## [1] 3.5

``` r
r_rocks <- 2 ^ 3
#r_rock
#R-rocks # both contain typos
```

\#calling functions

``` r
seq(1,10)
```

    ##  [1]  1  2  3  4  5  6  7  8  9 10

``` r
x <- "hello world"
y <- seq(1, 10, length.out = 5)
y
```

    ## [1]  1.00  3.25  5.50  7.75 10.00

``` r
(y <- seq(1, 10, length.out = 5))
```

    ## [1]  1.00  3.25  5.50  7.75 10.00

# exercises

``` r
#4.4.1
#the second line does not work because there no i in my_variable

#4.4.2
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.1 ──

    ## ✔ ggplot2 3.3.6     ✔ purrr   0.3.4
    ## ✔ tibble  3.1.7     ✔ dplyr   1.0.9
    ## ✔ tidyr   1.2.0     ✔ stringr 1.4.0
    ## ✔ readr   2.1.2     ✔ forcats 0.5.1

    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

``` r
library(ggplot2)
ggplot(data = mpg) + 
  geom_point( mapping = aes(displ, hwy))
```

![](chapter_4_ex_files/figure-gfm/unnamed-chunk-5-1.png)<!-- -->

``` r
filter(mpg, cyl == 8)
```

    ## # A tibble: 70 × 11
    ##    manufacturer model      displ  year   cyl trans drv     cty   hwy fl    class
    ##    <chr>        <chr>      <dbl> <int> <int> <chr> <chr> <int> <int> <chr> <chr>
    ##  1 audi         a6 quattro   4.2  2008     8 auto… 4        16    23 p     mids…
    ##  2 chevrolet    c1500 sub…   5.3  2008     8 auto… r        14    20 r     suv  
    ##  3 chevrolet    c1500 sub…   5.3  2008     8 auto… r        11    15 e     suv  
    ##  4 chevrolet    c1500 sub…   5.3  2008     8 auto… r        14    20 r     suv  
    ##  5 chevrolet    c1500 sub…   5.7  1999     8 auto… r        13    17 r     suv  
    ##  6 chevrolet    c1500 sub…   6    2008     8 auto… r        12    17 r     suv  
    ##  7 chevrolet    corvette     5.7  1999     8 manu… r        16    26 p     2sea…
    ##  8 chevrolet    corvette     5.7  1999     8 auto… r        15    23 p     2sea…
    ##  9 chevrolet    corvette     6.2  2008     8 manu… r        16    26 p     2sea…
    ## 10 chevrolet    corvette     6.2  2008     8 auto… r        15    25 p     2sea…
    ## # … with 60 more rows

``` r
filter(diamonds, carat > 3)
```

    ## # A tibble: 32 × 10
    ##    carat cut     color clarity depth table price     x     y     z
    ##    <dbl> <ord>   <ord> <ord>   <dbl> <dbl> <int> <dbl> <dbl> <dbl>
    ##  1  3.01 Premium I     I1       62.7    58  8040  9.1   8.97  5.67
    ##  2  3.11 Fair    J     I1       65.9    57  9823  9.15  9.02  5.98
    ##  3  3.01 Premium F     I1       62.2    56  9925  9.24  9.13  5.73
    ##  4  3.05 Premium E     I1       60.9    58 10453  9.26  9.25  5.66
    ##  5  3.02 Fair    I     I1       65.2    56 10577  9.11  9.02  5.91
    ##  6  3.01 Fair    H     I1       56.1    62 10761  9.54  9.38  5.31
    ##  7  3.65 Fair    H     I1       67.1    53 11668  9.53  9.48  6.38
    ##  8  3.24 Premium H     I1       62.1    58 12300  9.44  9.4   5.85
    ##  9  3.22 Ideal   I     I1       62.6    55 12545  9.49  9.42  5.92
    ## 10  3.5  Ideal   H     I1       62.8    57 12587  9.65  9.59  6.03
    ## # … with 22 more rows

``` r
#4.4.3
#alt shift K gives a overview of shortcuts
```
