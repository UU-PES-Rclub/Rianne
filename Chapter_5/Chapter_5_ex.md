Chapter5
================

\#Chapter 5 Data Transformation

\##5.1.1 Prerequisites

``` r
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
library(nycflights13)
flights <- nycflights13::flights
head(flights)
```

    ## # A tibble: 6 × 19
    ##    year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##   <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ## 1  2013     1     1      517            515         2      830            819
    ## 2  2013     1     1      533            529         4      850            830
    ## 3  2013     1     1      542            540         2      923            850
    ## 4  2013     1     1      544            545        -1     1004           1022
    ## 5  2013     1     1      554            600        -6      812            837
    ## 6  2013     1     1      554            558        -4      740            728
    ## # … with 11 more variables: arr_delay <dbl>, carrier <chr>, flight <int>,
    ## #   tailnum <chr>, origin <chr>, dest <chr>, air_time <dbl>, distance <dbl>,
    ## #   hour <dbl>, minute <dbl>, time_hour <dttm>

\##5.2 Filter rows

``` r
filter(flights, month == 1, day == 1)
```

    ## # A tibble: 842 × 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1      517            515         2      830            819
    ##  2  2013     1     1      533            529         4      850            830
    ##  3  2013     1     1      542            540         2      923            850
    ##  4  2013     1     1      544            545        -1     1004           1022
    ##  5  2013     1     1      554            600        -6      812            837
    ##  6  2013     1     1      554            558        -4      740            728
    ##  7  2013     1     1      555            600        -5      913            854
    ##  8  2013     1     1      557            600        -3      709            723
    ##  9  2013     1     1      557            600        -3      838            846
    ## 10  2013     1     1      558            600        -2      753            745
    ## # … with 832 more rows, and 11 more variables: arr_delay <dbl>, carrier <chr>,
    ## #   flight <int>, tailnum <chr>, origin <chr>, dest <chr>, air_time <dbl>,
    ## #   distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
#to save selection in a new separate dataframe
jan1 <- filter(flights, month == 1, day == 1)
#to save as a dataframe and print the results
(dec25 <- filter(flights, month == 12, day == 25))
```

    ## # A tibble: 719 × 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013    12    25      456            500        -4      649            651
    ##  2  2013    12    25      524            515         9      805            814
    ##  3  2013    12    25      542            540         2      832            850
    ##  4  2013    12    25      546            550        -4     1022           1027
    ##  5  2013    12    25      556            600        -4      730            745
    ##  6  2013    12    25      557            600        -3      743            752
    ##  7  2013    12    25      557            600        -3      818            831
    ##  8  2013    12    25      559            600        -1      855            856
    ##  9  2013    12    25      559            600        -1      849            855
    ## 10  2013    12    25      600            600         0      850            846
    ## # … with 709 more rows, and 11 more variables: arr_delay <dbl>, carrier <chr>,
    ## #   flight <int>, tailnum <chr>, origin <chr>, dest <chr>, air_time <dbl>,
    ## #   distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

\###5.2.1 Comparisons

``` r
sqrt(2) ^ 2 == 2
```

    ## [1] FALSE

``` r
1 / 49 * 49 == 1
```

    ## [1] FALSE

``` r
near(sqrt(2) ^ 2,  2)
```

    ## [1] TRUE

``` r
near(1 / 49 * 49, 1)
```

    ## [1] TRUE

\###5.2.2 Logical Operators

``` r
#flights that departed in nov or dec
filter(flights, month == 11 | month == 12)
```

    ## # A tibble: 55,403 × 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013    11     1        5           2359         6      352            345
    ##  2  2013    11     1       35           2250       105      123           2356
    ##  3  2013    11     1      455            500        -5      641            651
    ##  4  2013    11     1      539            545        -6      856            827
    ##  5  2013    11     1      542            545        -3      831            855
    ##  6  2013    11     1      549            600       -11      912            923
    ##  7  2013    11     1      550            600       -10      705            659
    ##  8  2013    11     1      554            600        -6      659            701
    ##  9  2013    11     1      554            600        -6      826            827
    ## 10  2013    11     1      554            600        -6      749            751
    ## # … with 55,393 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
#to select months without running in to numerical trouble
nov_dec <- filter(flights, month %in% c(11, 12))

filter(flights, !(arr_delay > 120 | dep_delay > 120))
```

    ## # A tibble: 316,050 × 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1      517            515         2      830            819
    ##  2  2013     1     1      533            529         4      850            830
    ##  3  2013     1     1      542            540         2      923            850
    ##  4  2013     1     1      544            545        -1     1004           1022
    ##  5  2013     1     1      554            600        -6      812            837
    ##  6  2013     1     1      554            558        -4      740            728
    ##  7  2013     1     1      555            600        -5      913            854
    ##  8  2013     1     1      557            600        -3      709            723
    ##  9  2013     1     1      557            600        -3      838            846
    ## 10  2013     1     1      558            600        -2      753            745
    ## # … with 316,040 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
filter(flights, arr_delay <= 120, dep_delay <= 120)
```

    ## # A tibble: 316,050 × 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1      517            515         2      830            819
    ##  2  2013     1     1      533            529         4      850            830
    ##  3  2013     1     1      542            540         2      923            850
    ##  4  2013     1     1      544            545        -1     1004           1022
    ##  5  2013     1     1      554            600        -6      812            837
    ##  6  2013     1     1      554            558        -4      740            728
    ##  7  2013     1     1      555            600        -5      913            854
    ##  8  2013     1     1      557            600        -3      709            723
    ##  9  2013     1     1      557            600        -3      838            846
    ## 10  2013     1     1      558            600        -2      753            745
    ## # … with 316,040 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

\###5.2.4 Exercises \####5.2.4.1 flight filter exercises

``` r
#all flights that
head(flights)
```

    ## # A tibble: 6 × 19
    ##    year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##   <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ## 1  2013     1     1      517            515         2      830            819
    ## 2  2013     1     1      533            529         4      850            830
    ## 3  2013     1     1      542            540         2      923            850
    ## 4  2013     1     1      544            545        -1     1004           1022
    ## 5  2013     1     1      554            600        -6      812            837
    ## 6  2013     1     1      554            558        -4      740            728
    ## # … with 11 more variables: arr_delay <dbl>, carrier <chr>, flight <int>,
    ## #   tailnum <chr>, origin <chr>, dest <chr>, air_time <dbl>, distance <dbl>,
    ## #   hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
arr_two <- filter(flights, arr_delay >= 120)
hou <- filter(flights, dest == "IAH" | dest == "HOU")
op_by_del_un_am <- filter(flights, carrier == "DL" | carrier == "AA" | carrier == "UA")
sum_dep <- filter(flights, month == 7 | month == 8 | month == 9)
only_arr_late <-  filter(flights, dep_delay == 0 & arr_delay >= 120)
del_30min <- filter(flights, dep_delay >= 60 & arr_delay >= 30)

#or for del_30min
del_30min <- flights %>%
  filter(dep_delay >= 60) %>%
  mutate(difference = dep_delay-arr_delay) %>%
  filter(difference >= 30)
del_30min
```

    ## # A tibble: 2,074 × 20
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1     1716           1545        91     2140           2039
    ##  2  2013     1     1     2205           1720       285       46           2040
    ##  3  2013     1     1     2326           2130       116      131             18
    ##  4  2013     1     3     1503           1221       162     1803           1555
    ##  5  2013     1     3     1821           1530       171     2131           1910
    ##  6  2013     1     3     1839           1700        99     2056           1950
    ##  7  2013     1     3     1850           1745        65     2148           2120
    ##  8  2013     1     3     1923           1815        68     2036           1958
    ##  9  2013     1     3     1941           1759       102     2246           2139
    ## 10  2013     1     3     1950           1845        65     2228           2227
    ## # … with 2,064 more rows, and 12 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>,
    ## #   difference <dbl>

``` r
flights_6am <- filter(flights, dep_time <= 600 & dep_time >= 0000)
```

\####5.2.4.2 use of between

``` r
head(flights)
```

    ## # A tibble: 6 × 19
    ##    year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##   <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ## 1  2013     1     1      517            515         2      830            819
    ## 2  2013     1     1      533            529         4      850            830
    ## 3  2013     1     1      542            540         2      923            850
    ## 4  2013     1     1      544            545        -1     1004           1022
    ## 5  2013     1     1      554            600        -6      812            837
    ## 6  2013     1     1      554            558        -4      740            728
    ## # … with 11 more variables: arr_delay <dbl>, carrier <chr>, flight <int>,
    ## #   tailnum <chr>, origin <chr>, dest <chr>, air_time <dbl>, distance <dbl>,
    ## #   hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
arr_two_b <- between(flights$arr_delay, 2, 344)
table(is.na(flights$dep_time))
```

    ## 
    ##  FALSE   TRUE 
    ## 328521   8255

``` r
#leos example
filter(flights,between(month,7,9))
```

    ## # A tibble: 86,326 × 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     7     1        1           2029       212      236           2359
    ##  2  2013     7     1        2           2359         3      344            344
    ##  3  2013     7     1       29           2245       104      151              1
    ##  4  2013     7     1       43           2130       193      322             14
    ##  5  2013     7     1       44           2150       174      300            100
    ##  6  2013     7     1       46           2051       235      304           2358
    ##  7  2013     7     1       48           2001       287      308           2305
    ##  8  2013     7     1       58           2155       183      335             43
    ##  9  2013     7     1      100           2146       194      327             30
    ## 10  2013     7     1      100           2245       135      337            135
    ## # … with 86,316 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

\###5.3 Arrange

``` r
arrange(flights, year, month, day)
```

    ## # A tibble: 336,776 × 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1      517            515         2      830            819
    ##  2  2013     1     1      533            529         4      850            830
    ##  3  2013     1     1      542            540         2      923            850
    ##  4  2013     1     1      544            545        -1     1004           1022
    ##  5  2013     1     1      554            600        -6      812            837
    ##  6  2013     1     1      554            558        -4      740            728
    ##  7  2013     1     1      555            600        -5      913            854
    ##  8  2013     1     1      557            600        -3      709            723
    ##  9  2013     1     1      557            600        -3      838            846
    ## 10  2013     1     1      558            600        -2      753            745
    ## # … with 336,766 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
arrange(flights, desc(dep_delay))
```

    ## # A tibble: 336,776 × 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     9      641            900      1301     1242           1530
    ##  2  2013     6    15     1432           1935      1137     1607           2120
    ##  3  2013     1    10     1121           1635      1126     1239           1810
    ##  4  2013     9    20     1139           1845      1014     1457           2210
    ##  5  2013     7    22      845           1600      1005     1044           1815
    ##  6  2013     4    10     1100           1900       960     1342           2211
    ##  7  2013     3    17     2321            810       911      135           1020
    ##  8  2013     6    27      959           1900       899     1236           2226
    ##  9  2013     7    22     2257            759       898      121           1026
    ## 10  2013    12     5      756           1700       896     1058           2020
    ## # … with 336,766 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
df <-  tibble(x=c(5,2,NA))
arrange(df, x)
```

    ## # A tibble: 3 × 1
    ##       x
    ##   <dbl>
    ## 1     2
    ## 2     5
    ## 3    NA

``` r
arrange(df, desc(x))
```

    ## # A tibble: 3 × 1
    ##       x
    ##   <dbl>
    ## 1     5
    ## 2     2
    ## 3    NA

\####5.3.1 Exercises

``` r
#missing values
arrange(flights, desc(is.na(arr_time)))
```

    ## # A tibble: 336,776 × 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1     2016           1930        46       NA           2220
    ##  2  2013     1     1       NA           1630        NA       NA           1815
    ##  3  2013     1     1       NA           1935        NA       NA           2240
    ##  4  2013     1     1       NA           1500        NA       NA           1825
    ##  5  2013     1     1       NA            600        NA       NA            901
    ##  6  2013     1     2     2041           2045        -4       NA           2359
    ##  7  2013     1     2     2145           2129        16       NA             33
    ##  8  2013     1     2       NA           1540        NA       NA           1747
    ##  9  2013     1     2       NA           1620        NA       NA           1746
    ## 10  2013     1     2       NA           1355        NA       NA           1459
    ## # … with 336,766 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
#most delayed flights
arrange(flights,desc(dep_delay),desc(arr_delay))
```

    ## # A tibble: 336,776 × 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     9      641            900      1301     1242           1530
    ##  2  2013     6    15     1432           1935      1137     1607           2120
    ##  3  2013     1    10     1121           1635      1126     1239           1810
    ##  4  2013     9    20     1139           1845      1014     1457           2210
    ##  5  2013     7    22      845           1600      1005     1044           1815
    ##  6  2013     4    10     1100           1900       960     1342           2211
    ##  7  2013     3    17     2321            810       911      135           1020
    ##  8  2013     6    27      959           1900       899     1236           2226
    ##  9  2013     7    22     2257            759       898      121           1026
    ## 10  2013    12     5      756           1700       896     1058           2020
    ## # … with 336,766 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
arrange(flights,dep_time)
```

    ## # A tibble: 336,776 × 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1    13        1           2249        72      108           2357
    ##  2  2013     1    31        1           2100       181      124           2225
    ##  3  2013    11    13        1           2359         2      442            440
    ##  4  2013    12    16        1           2359         2      447            437
    ##  5  2013    12    20        1           2359         2      430            440
    ##  6  2013    12    26        1           2359         2      437            440
    ##  7  2013    12    30        1           2359         2      441            437
    ##  8  2013     2    11        1           2100       181      111           2225
    ##  9  2013     2    24        1           2245        76      121           2354
    ## 10  2013     3     8        1           2355         6      431            440
    ## # … with 336,766 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
#sort flights to find the fastest flights
arrange(flights,air_time)
```

    ## # A tibble: 336,776 × 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1    16     1355           1315        40     1442           1411
    ##  2  2013     4    13      537            527        10      622            628
    ##  3  2013    12     6      922            851        31     1021            954
    ##  4  2013     2     3     2153           2129        24     2247           2224
    ##  5  2013     2     5     1303           1315       -12     1342           1411
    ##  6  2013     2    12     2123           2130        -7     2211           2225
    ##  7  2013     3     2     1450           1500       -10     1547           1608
    ##  8  2013     3     8     2026           1935        51     2131           2056
    ##  9  2013     3    18     1456           1329        87     1533           1426
    ## 10  2013     3    19     2226           2145        41     2305           2246
    ## # … with 336,766 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
arrange(flights,desc(distance))
```

    ## # A tibble: 336,776 × 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1      857            900        -3     1516           1530
    ##  2  2013     1     2      909            900         9     1525           1530
    ##  3  2013     1     3      914            900        14     1504           1530
    ##  4  2013     1     4      900            900         0     1516           1530
    ##  5  2013     1     5      858            900        -2     1519           1530
    ##  6  2013     1     6     1019            900        79     1558           1530
    ##  7  2013     1     7     1042            900       102     1620           1530
    ##  8  2013     1     8      901            900         1     1504           1530
    ##  9  2013     1     9      641            900      1301     1242           1530
    ## 10  2013     1    10      859            900        -1     1449           1530
    ## # … with 336,766 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
arrange(flights,desc(distance),air_time)
```

    ## # A tibble: 336,776 × 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     5     7      959           1000        -1     1401           1500
    ##  2  2013     6     6     1044           1000        44     1441           1435
    ##  3  2013     9    29      957           1000        -3     1405           1445
    ##  4  2013     6     7      952           1000        -8     1354           1435
    ##  5  2013     6     8      951           1000        -9     1352           1435
    ##  6  2013     9     6      955           1000        -5     1359           1445
    ##  7  2013     2    26     1000            900        60     1513           1540
    ##  8  2013     5     6      956           1000        -4     1358           1500
    ##  9  2013     9    28      955           1000        -5     1412           1445
    ## 10  2013     7     3      957           1000        -3     1410           1430
    ## # … with 336,766 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
#flight travelled farthest and flight travelled shortest
arrange(flights,desc(distance))
```

    ## # A tibble: 336,776 × 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     1      857            900        -3     1516           1530
    ##  2  2013     1     2      909            900         9     1525           1530
    ##  3  2013     1     3      914            900        14     1504           1530
    ##  4  2013     1     4      900            900         0     1516           1530
    ##  5  2013     1     5      858            900        -2     1519           1530
    ##  6  2013     1     6     1019            900        79     1558           1530
    ##  7  2013     1     7     1042            900       102     1620           1530
    ##  8  2013     1     8      901            900         1     1504           1530
    ##  9  2013     1     9      641            900      1301     1242           1530
    ## 10  2013     1    10      859            900        -1     1449           1530
    ## # … with 336,766 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
arrange(flights,distance)
```

    ## # A tibble: 336,776 × 19
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     7    27       NA            106        NA       NA            245
    ##  2  2013     1     3     2127           2129        -2     2222           2224
    ##  3  2013     1     4     1240           1200        40     1333           1306
    ##  4  2013     1     4     1829           1615       134     1937           1721
    ##  5  2013     1     4     2128           2129        -1     2218           2224
    ##  6  2013     1     5     1155           1200        -5     1241           1306
    ##  7  2013     1     6     2125           2129        -4     2224           2224
    ##  8  2013     1     7     2124           2129        -5     2212           2224
    ##  9  2013     1     8     2127           2130        -3     2304           2225
    ## 10  2013     1     9     2126           2129        -3     2217           2224
    ## # … with 336,766 more rows, and 11 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>

\#5.4

``` r
#Select columns by name
select(flights, year, month, day)
```

    ## # A tibble: 336,776 × 3
    ##     year month   day
    ##    <int> <int> <int>
    ##  1  2013     1     1
    ##  2  2013     1     1
    ##  3  2013     1     1
    ##  4  2013     1     1
    ##  5  2013     1     1
    ##  6  2013     1     1
    ##  7  2013     1     1
    ##  8  2013     1     1
    ##  9  2013     1     1
    ## 10  2013     1     1
    ## # … with 336,766 more rows

``` r
#Select all columns between year and day (inclusive)
select(flights, year:day)
```

    ## # A tibble: 336,776 × 3
    ##     year month   day
    ##    <int> <int> <int>
    ##  1  2013     1     1
    ##  2  2013     1     1
    ##  3  2013     1     1
    ##  4  2013     1     1
    ##  5  2013     1     1
    ##  6  2013     1     1
    ##  7  2013     1     1
    ##  8  2013     1     1
    ##  9  2013     1     1
    ## 10  2013     1     1
    ## # … with 336,766 more rows

``` r
#Select all columns except those from year to day (inclusive)
select(flights, -(year:day))
```

    ## # A tibble: 336,776 × 16
    ##    dep_time sched_dep_time dep_delay arr_time sched_arr_time arr_delay carrier
    ##       <int>          <int>     <dbl>    <int>          <int>     <dbl> <chr>  
    ##  1      517            515         2      830            819        11 UA     
    ##  2      533            529         4      850            830        20 UA     
    ##  3      542            540         2      923            850        33 AA     
    ##  4      544            545        -1     1004           1022       -18 B6     
    ##  5      554            600        -6      812            837       -25 DL     
    ##  6      554            558        -4      740            728        12 UA     
    ##  7      555            600        -5      913            854        19 B6     
    ##  8      557            600        -3      709            723       -14 EV     
    ##  9      557            600        -3      838            846        -8 B6     
    ## 10      558            600        -2      753            745         8 AA     
    ## # … with 336,766 more rows, and 9 more variables: flight <int>, tailnum <chr>,
    ## #   origin <chr>, dest <chr>, air_time <dbl>, distance <dbl>, hour <dbl>,
    ## #   minute <dbl>, time_hour <dttm>

``` r
#to move certain colums to the start of the data frame
select(flights, time_hour, air_time, everything())
```

    ## # A tibble: 336,776 × 19
    ##    time_hour           air_time  year month   day dep_time sched_dep_time
    ##    <dttm>                 <dbl> <int> <int> <int>    <int>          <int>
    ##  1 2013-01-01 05:00:00      227  2013     1     1      517            515
    ##  2 2013-01-01 05:00:00      227  2013     1     1      533            529
    ##  3 2013-01-01 05:00:00      160  2013     1     1      542            540
    ##  4 2013-01-01 05:00:00      183  2013     1     1      544            545
    ##  5 2013-01-01 06:00:00      116  2013     1     1      554            600
    ##  6 2013-01-01 05:00:00      150  2013     1     1      554            558
    ##  7 2013-01-01 06:00:00      158  2013     1     1      555            600
    ##  8 2013-01-01 06:00:00       53  2013     1     1      557            600
    ##  9 2013-01-01 06:00:00      140  2013     1     1      557            600
    ## 10 2013-01-01 06:00:00      138  2013     1     1      558            600
    ## # … with 336,766 more rows, and 12 more variables: dep_delay <dbl>,
    ## #   arr_time <int>, sched_arr_time <int>, arr_delay <dbl>, carrier <chr>,
    ## #   flight <int>, tailnum <chr>, origin <chr>, dest <chr>, distance <dbl>,
    ## #   hour <dbl>, minute <dbl>

\###5.4.1 Exercises \####1. Brainstorm as many ways as possible to
select dep_time, dep_delay, arr_time, and arr_delay from flights

``` r
head(flights)
```

    ## # A tibble: 6 × 19
    ##    year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##   <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ## 1  2013     1     1      517            515         2      830            819
    ## 2  2013     1     1      533            529         4      850            830
    ## 3  2013     1     1      542            540         2      923            850
    ## 4  2013     1     1      544            545        -1     1004           1022
    ## 5  2013     1     1      554            600        -6      812            837
    ## 6  2013     1     1      554            558        -4      740            728
    ## # … with 11 more variables: arr_delay <dbl>, carrier <chr>, flight <int>,
    ## #   tailnum <chr>, origin <chr>, dest <chr>, air_time <dbl>, distance <dbl>,
    ## #   hour <dbl>, minute <dbl>, time_hour <dttm>

``` r
select(flights,dep_time, dep_delay, arr_time, arr_delay)
```

    ## # A tibble: 336,776 × 4
    ##    dep_time dep_delay arr_time arr_delay
    ##       <int>     <dbl>    <int>     <dbl>
    ##  1      517         2      830        11
    ##  2      533         4      850        20
    ##  3      542         2      923        33
    ##  4      544        -1     1004       -18
    ##  5      554        -6      812       -25
    ##  6      554        -4      740        12
    ##  7      555        -5      913        19
    ##  8      557        -3      709       -14
    ##  9      557        -3      838        -8
    ## 10      558        -2      753         8
    ## # … with 336,766 more rows

``` r
#feels like more work or just as much
select(flights,dep_time:arr_delay,-sched_arr_time,-sched_dep_time)
```

    ## # A tibble: 336,776 × 4
    ##    dep_time dep_delay arr_time arr_delay
    ##       <int>     <dbl>    <int>     <dbl>
    ##  1      517         2      830        11
    ##  2      533         4      850        20
    ##  3      542         2      923        33
    ##  4      544        -1     1004       -18
    ##  5      554        -6      812       -25
    ##  6      554        -4      740        12
    ##  7      555        -5      913        19
    ##  8      557        -3      709       -14
    ##  9      557        -3      838        -8
    ## 10      558        -2      753         8
    ## # … with 336,766 more rows

\###2. What happens if you include the name of a variable multiple times
in a select() call?

``` r
select(flights, arr_time, arr_time, arr_time)
```

    ## # A tibble: 336,776 × 1
    ##    arr_time
    ##       <int>
    ##  1      830
    ##  2      850
    ##  3      923
    ##  4     1004
    ##  5      812
    ##  6      740
    ##  7      913
    ##  8      709
    ##  9      838
    ## 10      753
    ## # … with 336,766 more rows

\###3. What does the any_of() function do? Why might it be helpful in
conjunction with this vector?

``` r
?any_of
```

    ## starting httpd help server ... done

``` r
#any of helps with selecting variables in a character vector and allows for missing values
vars <- c("year", "month", "day", "dep_delay", "arr_delay")
select(flights,any_of(vars))
```

    ## # A tibble: 336,776 × 5
    ##     year month   day dep_delay arr_delay
    ##    <int> <int> <int>     <dbl>     <dbl>
    ##  1  2013     1     1         2        11
    ##  2  2013     1     1         4        20
    ##  3  2013     1     1         2        33
    ##  4  2013     1     1        -1       -18
    ##  5  2013     1     1        -6       -25
    ##  6  2013     1     1        -4        12
    ##  7  2013     1     1        -5        19
    ##  8  2013     1     1        -3       -14
    ##  9  2013     1     1        -3        -8
    ## 10  2013     1     1        -2         8
    ## # … with 336,766 more rows

\####4. Does the result of running the following code surprise you? How
do the select helpers deal with case by default? How can you change that
default?

``` r
select(flights, contains("TIME"))
```

    ## # A tibble: 336,776 × 6
    ##    dep_time sched_dep_time arr_time sched_arr_time air_time time_hour          
    ##       <int>          <int>    <int>          <int>    <dbl> <dttm>             
    ##  1      517            515      830            819      227 2013-01-01 05:00:00
    ##  2      533            529      850            830      227 2013-01-01 05:00:00
    ##  3      542            540      923            850      160 2013-01-01 05:00:00
    ##  4      544            545     1004           1022      183 2013-01-01 05:00:00
    ##  5      554            600      812            837      116 2013-01-01 06:00:00
    ##  6      554            558      740            728      150 2013-01-01 05:00:00
    ##  7      555            600      913            854      158 2013-01-01 06:00:00
    ##  8      557            600      709            723       53 2013-01-01 06:00:00
    ##  9      557            600      838            846      140 2013-01-01 06:00:00
    ## 10      558            600      753            745      138 2013-01-01 06:00:00
    ## # … with 336,766 more rows

``` r
select(flights, contains("TIME", ignore.case = TRUE))
```

    ## # A tibble: 336,776 × 6
    ##    dep_time sched_dep_time arr_time sched_arr_time air_time time_hour          
    ##       <int>          <int>    <int>          <int>    <dbl> <dttm>             
    ##  1      517            515      830            819      227 2013-01-01 05:00:00
    ##  2      533            529      850            830      227 2013-01-01 05:00:00
    ##  3      542            540      923            850      160 2013-01-01 05:00:00
    ##  4      544            545     1004           1022      183 2013-01-01 05:00:00
    ##  5      554            600      812            837      116 2013-01-01 06:00:00
    ##  6      554            558      740            728      150 2013-01-01 05:00:00
    ##  7      555            600      913            854      158 2013-01-01 06:00:00
    ##  8      557            600      709            723       53 2013-01-01 06:00:00
    ##  9      557            600      838            846      140 2013-01-01 06:00:00
    ## 10      558            600      753            745      138 2013-01-01 06:00:00
    ## # … with 336,766 more rows

``` r
select(flights, contains("TIME", ignore.case = FALSE))
```

    ## # A tibble: 336,776 × 0

``` r
#default is at ignore.case=TRUE
```

\###5.5.2 Exercises \####1. Currently dep_time and sched_dep_time are
convenient to look at, but hard to compute with because they’re not
really continuous numbers. Convert them to a more convenient
representation of number of minutes since midnight.

``` r
deps <- select(flights, dep_time, sched_dep_time)
deps_1 <- mutate(deps,
                 h_dep_time = dep_time %/% 100,
                 min_dep_time = dep_time %% 100,
                 totalmin_dep_time = h_dep_time*60+min_dep_time,
                 h_sch_dep_time = dep_time %/% 100,
                 min_sch_dep_time = dep_time %% 100,
                 totalmin_dep_time = h_sch_dep_time*60+min_dep_time)
deps_1
```

    ## # A tibble: 336,776 × 7
    ##    dep_time sched_dep_time h_dep_time min_dep_time totalmin_dep_time
    ##       <int>          <int>      <dbl>        <dbl>             <dbl>
    ##  1      517            515          5           17               317
    ##  2      533            529          5           33               333
    ##  3      542            540          5           42               342
    ##  4      544            545          5           44               344
    ##  5      554            600          5           54               354
    ##  6      554            558          5           54               354
    ##  7      555            600          5           55               355
    ##  8      557            600          5           57               357
    ##  9      557            600          5           57               357
    ## 10      558            600          5           58               358
    ## # … with 336,766 more rows, and 2 more variables: h_sch_dep_time <dbl>,
    ## #   min_sch_dep_time <dbl>

#### 2. Compare air_time with arr_time - dep_time. What do you expect to see? What do you see? What do you need to do to fix it?

``` r
arrs <- mutate(flights,h_dep_time = dep_time %/% 100,
              min_dep_time = dep_time %% 100,
              totalmin_dep_time = h_dep_time*60+min_dep_time,
              h_arr_time = arr_time %/% 100,
              min_arr_time = arr_time %% 100,
              totalmin_arr_time = h_arr_time*60+min_arr_time,
              air_time2 = totalmin_arr_time - totalmin_dep_time)
arrs <- select(arrs,arr_time,dep_time,totalmin_arr_time,totalmin_dep_time,air_time,air_time2)
head(arrs)
```

    ## # A tibble: 6 × 6
    ##   arr_time dep_time totalmin_arr_time totalmin_dep_time air_time air_time2
    ##      <int>    <int>             <dbl>             <dbl>    <dbl>     <dbl>
    ## 1      830      517               510               317      227       193
    ## 2      850      533               530               333      227       197
    ## 3      923      542               563               342      160       221
    ## 4     1004      544               604               344      183       260
    ## 5      812      554               492               354      116       138
    ## 6      740      554               460               354      150       106

#### 3. Compare dep_time, sched_dep_time, and dep_delay. How would you expect those three numbers to be related?

``` r
dep <- select(flights,dep_time,sched_dep_time,dep_delay)
dep1 <- mutate(dep,dep_delay2 = dep_time - sched_dep_time)
dep1
```

    ## # A tibble: 336,776 × 4
    ##    dep_time sched_dep_time dep_delay dep_delay2
    ##       <int>          <int>     <dbl>      <int>
    ##  1      517            515         2          2
    ##  2      533            529         4          4
    ##  3      542            540         2          2
    ##  4      544            545        -1         -1
    ##  5      554            600        -6        -46
    ##  6      554            558        -4         -4
    ##  7      555            600        -5        -45
    ##  8      557            600        -3        -43
    ##  9      557            600        -3        -43
    ## 10      558            600        -2        -42
    ## # … with 336,766 more rows

``` r
dep2 <- mutate(flights, h_dep_time = dep_time %/% 100,
              min_dep_time = dep_time %% 100,
              totalmin_dep_time = h_dep_time*60+min_dep_time,
              h_sched_dep_time = sched_dep_time %/% 100,
              min_sched_dep_time = sched_dep_time %% 100,
              totalmin_sched_dep_time = h_sched_dep_time*60+min_sched_dep_time,
              dep_delay2 = totalmin_dep_time - totalmin_sched_dep_time)
dep3 <- select(dep2,dep_delay,dep_delay2)
dep3
```

    ## # A tibble: 336,776 × 2
    ##    dep_delay dep_delay2
    ##        <dbl>      <dbl>
    ##  1         2          2
    ##  2         4          4
    ##  3         2          2
    ##  4        -1         -1
    ##  5        -6         -6
    ##  6        -4         -4
    ##  7        -5         -5
    ##  8        -3         -3
    ##  9        -3         -3
    ## 10        -2         -2
    ## # … with 336,766 more rows

``` r
#dep3 results are in minutes
```

\####4. Find the 10 most delayed flights using a ranking function. How
do you want to handle ties? Carefully read the documentation for
min_rank().

``` r
rank_delay <- mutate(flights, rank = min_rank(dep_delay))
rank_delay_desc <- arrange(rank_delay,desc(rank))
rank_delay_desc
```

    ## # A tibble: 336,776 × 20
    ##     year month   day dep_time sched_dep_time dep_delay arr_time sched_arr_time
    ##    <int> <int> <int>    <int>          <int>     <dbl>    <int>          <int>
    ##  1  2013     1     9      641            900      1301     1242           1530
    ##  2  2013     6    15     1432           1935      1137     1607           2120
    ##  3  2013     1    10     1121           1635      1126     1239           1810
    ##  4  2013     9    20     1139           1845      1014     1457           2210
    ##  5  2013     7    22      845           1600      1005     1044           1815
    ##  6  2013     4    10     1100           1900       960     1342           2211
    ##  7  2013     3    17     2321            810       911      135           1020
    ##  8  2013     6    27      959           1900       899     1236           2226
    ##  9  2013     7    22     2257            759       898      121           1026
    ## 10  2013    12     5      756           1700       896     1058           2020
    ## # … with 336,766 more rows, and 12 more variables: arr_delay <dbl>,
    ## #   carrier <chr>, flight <int>, tailnum <chr>, origin <chr>, dest <chr>,
    ## #   air_time <dbl>, distance <dbl>, hour <dbl>, minute <dbl>, time_hour <dttm>,
    ## #   rank <int>

\####5. What does 1:3 + 1:10 return? Why?

``` r
1:3 + 1:10
```

    ## Warning in 1:3 + 1:10: longer object length is not a multiple of shorter object
    ## length

    ##  [1]  2  4  6  5  7  9  8 10 12 11

``` r
1:3
```

    ## [1] 1 2 3

``` r
1:10
```

    ##  [1]  1  2  3  4  5  6  7  8  9 10

``` r
1:10+1:3
```

    ## Warning in 1:10 + 1:3: longer object length is not a multiple of shorter object
    ## length

    ##  [1]  2  4  6  5  7  9  8 10 12 11

\####6. What trigonometric functions does R provide?

``` r
?base::Trig
#shows all the trig functions
```

\###5.6 Grouped summaries with summarise()
