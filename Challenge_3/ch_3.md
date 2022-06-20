Untitled
================

\#modifications

``` r
calc <- select(df, pixlen, pet.len) %>%
  mutate(petinmm = 10*pet.len/pixlen)
```

Note that the `echo = FALSE` parameter was added to the code chunk to
prevent printing of the R code that generated the plot.
