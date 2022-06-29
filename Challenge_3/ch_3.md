Untitled
================

``` r
#pet.angle over image
ggplot(df) +
  geom_line(aes(image,pet.angle,colour=plant))
```

![](ch_3_files/figure-gfm/unnamed-chunk-1-1.png)<!-- -->

``` r
#leaf.angle over image
ggplot(df) +
  geom_line(aes(image,leaf.angle,colour=plant))
```

![](ch_3_files/figure-gfm/unnamed-chunk-1-2.png)<!-- -->

``` r
#leaf.angle gives a smoother line
```

\#modifications

``` r
calc <- select(df, pixlen, pet.len, plant, image) %>%
  mutate(petinmm = 10*pet.len/pixlen)

#pet.angle over image
ggplot(calc) +
  geom_line(aes(image,petinmm,colour=plant))
```

![](ch_3_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

``` r
ggplot(calc) +
  geom_smooth(aes(image,petinmm,colour=plant))
```

    ## `geom_smooth()` using method = 'gam' and formula 'y ~ s(x, bs = "cs")'

![](ch_3_files/figure-gfm/unnamed-chunk-2-2.png)<!-- -->

``` r
head(df)
```

    ##   image xpet ypet xleaf yleaf     m.int xmer ymer ld.thr light.thr dark.thr
    ## 1     5   88  311   256   343 0.4494187    5  334   0.35     0.225     0.06
    ## 2     6   88  311   256   343 0.4492669    5  334   0.35     0.225     0.06
    ## 3     7   88  311   256   343 0.4496357    5  334   0.35     0.225     0.06
    ## 4     8   88  311   256   343 0.4487699    5  334   0.35     0.225     0.06
    ## 5     9   88  311   254   338 0.4497911    5  334   0.35     0.225     0.06
    ## 6    10   88  311   256   343 0.4499110    5  334   0.35     0.225     0.06
    ##        xll      yll      xur      yur xpet.ldc ypet.ldc xleaf.ldc yleaf.ldc
    ## 1 328.7688 812.8752 813.0228 358.1189       88      311       256       343
    ## 2 328.7688 812.8752 813.0228 358.1189       88      311       256       343
    ## 3 328.7688 812.8752 813.0228 358.1189       88      311       256       343
    ## 4 328.7688 812.8752 813.0228 358.1189       88      311       256       343
    ## 5 328.7688 812.8752 813.0228 358.1189       88      311       254       338
    ## 6 328.7688 812.8752 813.0228 358.1189       88      311       256       343
    ##   xpet.ldc.1 ypet.ldc.1 xleaf.ldc.1 yleaf.ldc.1 win.size xpet.1 ypet.1 xleaf.1
    ## 1         88        311         256         343        9     88    311     256
    ## 2         88        311         256         343        9     88    311     256
    ## 3         88        311         256         343        9     88    311     256
    ## 4         88        311         256         343        9     88    311     256
    ## 5         88        311         256         343        9     88    311     256
    ## 6         88        311         256         343        9     88    311     256
    ##   yleaf.1   m.int.1 xpix ypix  pet.len pet.angle leaf.len leaf.angle lamina.len
    ## 1     343 0.4494187    5  334 86.12781  15.49636 251.1613  -2.054592   171.0205
    ## 2     343 0.4492669    5  334 86.12781  15.49636 251.1613  -2.054592   171.0205
    ## 3     343 0.4496357    5  334 86.12781  15.49636 251.1613  -2.054592   171.0205
    ## 4     343 0.4487699    5  334 86.12781  15.49636 251.1613  -2.054592   171.0205
    ## 5     343 0.4497911    5  334 86.12781  15.49636 251.1613  -2.054592   171.0205
    ## 6     343 0.4499110    5  334 86.12781  15.49636 251.1613  -2.054592   171.0205
    ##   lamina.angle   pixlen   plant
    ## 1    -10.78977 184.0872 Plant01
    ## 2    -10.78977 184.0872 Plant01
    ## 3    -10.78977 184.0872 Plant01
    ## 4    -10.78977 184.0872 Plant01
    ## 5    -10.78977 184.0872 Plant01
    ## 6    -10.78977 184.0872 Plant01

``` r
dfmm <- df %>%
  select(image, pet.len:plant) %>%
  mutate(petinmm = 10*pet.len/pixlen, leafleninmm = 10*leaf.len/pixlen, laminmm = 10*lamina.len/pixlen) 

#plots
ggplot(dfmm) +
  geom_line(aes(image,petinmm,colour=plant))
```

![](ch_3_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

``` r
ggplot(dfmm) +
  geom_line(aes(image,leafleninmm,colour=plant))
```

![](ch_3_files/figure-gfm/unnamed-chunk-3-2.png)<!-- -->

``` r
ggplot(dfmm) +
  geom_line(aes(image,laminmm,colour=plant))
```

![](ch_3_files/figure-gfm/unnamed-chunk-3-3.png)<!-- -->

``` r
ggplot(dfmm) +
  geom_line(aes(image,petinmm,colour=plant))+
  geom_smooth(aes(image,petinmm,colour=plant))
```

    ## `geom_smooth()` using method = 'gam' and formula 'y ~ s(x, bs = "cs")'

![](ch_3_files/figure-gfm/unnamed-chunk-3-4.png)<!-- -->

``` r
ggplot(dfmm) +
  geom_line(aes(image,leafleninmm,colour=plant))+
   geom_smooth(aes(image,leafleninmm,colour=plant))
```

    ## `geom_smooth()` using method = 'gam' and formula 'y ~ s(x, bs = "cs")'

![](ch_3_files/figure-gfm/unnamed-chunk-3-5.png)<!-- -->

``` r
ggplot(dfmm) +
  geom_line(aes(image,laminmm,colour=plant))+
  geom_smooth(aes(image,laminmm,colour=plant))
```

    ## `geom_smooth()` using method = 'gam' and formula 'y ~ s(x, bs = "cs")'

![](ch_3_files/figure-gfm/unnamed-chunk-3-6.png)<!-- --> \#MEAN
pet.angle

``` r
by_image <- group_by(dfmm, image, plant, pet.angle)
summarise(by_image, mean.angle = mean(pet.angle, na.rm = TRUE))
```

    ## `summarise()` has grouped output by 'image', 'plant'. You can override using
    ## the `.groups` argument.

    ## # A tibble: 2,820 × 4
    ## # Groups:   image, plant [2,820]
    ##    image plant   pet.angle mean.angle
    ##    <int> <chr>       <dbl>      <dbl>
    ##  1     5 Plant01      15.5       15.5
    ##  2     5 Plant02      13.9       13.9
    ##  3     6 Plant01      15.5       15.5
    ##  4     6 Plant02      13.9       13.9
    ##  5     7 Plant01      15.5       15.5
    ##  6     7 Plant02      13.9       13.9
    ##  7     8 Plant01      15.5       15.5
    ##  8     8 Plant02      13.9       13.9
    ##  9     9 Plant01      15.5       15.5
    ## 10     9 Plant02      13.9       13.9
    ## # … with 2,810 more rows
