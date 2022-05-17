chapter_3\_book
================

``` r
#dataframe
mpg <- ggplot2::mpg
nrow(mpg)
```

    ## [1] 234

``` r
ncol(mpg)
```

    ## [1] 11

``` r
dim(mpg)
```

    ## [1] 234  11

``` r
#drv means the the type of drive train
#cyl is the number of cylinders
#hwy is the highway miles per gallos #cty is the city miles per gallon
```

``` r
ggplot(mpg)
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

``` r
ggplot(mpg) +
  geom_point(mapping = aes(displ, hwy))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

``` r
ggplot(mpg) +
  geom_point(mapping = aes(hwy, cyl))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-4-1.png)<!-- -->

``` r
ggplot(mpg) +
  geom_point(mapping = aes(class, drv))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-5-1.png)<!-- -->

``` r
#uses colors to distinguish discrete variable -> class 
ggplot(mpg) +
  geom_point(mapping = aes(displ, hwy, color = class))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-6-1.png)<!-- -->

``` r
  geom_point(aes(displ, hwy, color = class))
```

    ## mapping: x = ~displ, y = ~hwy, colour = ~class 
    ## geom_point: na.rm = FALSE
    ## stat_identity: na.rm = FALSE
    ## position_identity

``` r
#uses size to distinguish discrete variable -> class 
ggplot(mpg) +
  geom_point(mapping = aes(displ, hwy, size = class))
```

    ## Warning: Using size for a discrete variable is not advised.

![](ch3_fin_files/figure-gfm/unnamed-chunk-6-2.png)<!-- -->

``` r
  geom_point(aes(displ, hwy, size = class))
```

    ## mapping: x = ~displ, y = ~hwy, size = ~class 
    ## geom_point: na.rm = FALSE
    ## stat_identity: na.rm = FALSE
    ## position_identity

``` r
#uses alpha (aesthetic) to distinguish discrete variable -> class 
ggplot(mpg) +
  geom_point(mapping = aes(displ, hwy, alpha = class))
```

    ## Warning: Using alpha for a discrete variable is not advised.

![](ch3_fin_files/figure-gfm/unnamed-chunk-6-3.png)<!-- -->

``` r
  geom_point(aes(displ, hwy, alpha = class))
```

    ## mapping: x = ~displ, y = ~hwy, alpha = ~class 
    ## geom_point: na.rm = FALSE
    ## stat_identity: na.rm = FALSE
    ## position_identity

``` r
#uses shape (aesthetic) to distinguish discrete variable -> class  #ggplot can only use 6 shapes at a time
ggplot(mpg) +
  geom_point(mapping = aes(displ, hwy, shape = class))
```

    ## Warning: The shape palette can deal with a maximum of 6 discrete values because
    ## more than 6 becomes difficult to discriminate; you have 7. Consider
    ## specifying shapes manually if you must have them.

    ## Warning: Removed 62 rows containing missing values (geom_point).

![](ch3_fin_files/figure-gfm/unnamed-chunk-6-4.png)<!-- -->

``` r
  geom_point(aes(displ, hwy, shape = class))
```

    ## mapping: x = ~displ, y = ~hwy, shape = ~class 
    ## geom_point: na.rm = FALSE
    ## stat_identity: na.rm = FALSE
    ## position_identity

``` r
#example how not to define a specific colour for the discrete variable color
ggplot(mpg) +
  geom_point(mapping = aes(displ, hwy, color = "blue"))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-6-5.png)<!-- -->

``` r
  geom_point(aes(displ, hwy, color = "blue"))
```

    ## mapping: x = ~displ, y = ~hwy, colour = blue 
    ## geom_point: na.rm = FALSE
    ## stat_identity: na.rm = FALSE
    ## position_identity

``` r
#how to use a specific colors to distinguish discrete variable -> class 
ggplot(mpg) +
  geom_point(mapping = aes(displ, hwy), color = "blue")
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-6-6.png)<!-- -->

``` r
  geom_point(aes(displ, hwy), color = "blue")
```

    ## mapping: x = ~displ, y = ~hwy 
    ## geom_point: na.rm = FALSE
    ## stat_identity: na.rm = FALSE
    ## position_identity

``` r
#3.3.1.1 see answer in chunk above
#3.3.1.2 
# categorical: model,manufacturer,Trans, drv,fl,class
# continuous: displ, year, cyl, cty, hwy
#3.3.1.3
#continous
#cyl
ggplot(mpg) +
  geom_point(mapping = aes(displ, hwy, color = cyl))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-7-1.png)<!-- -->

``` r
ggplot(mpg) +
  geom_point(mapping = aes(displ, hwy, size = cyl))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-7-2.png)<!-- -->

``` r
#a continous variable cannot be mapped to a schape
#ggplot(mpg) +
  #geom_point(mapping = aes(displ, hwy, shape = cyl))
#cty
ggplot(mpg) +
  geom_point(mapping = aes(displ, hwy, color = cty))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-7-3.png)<!-- -->

``` r
ggplot(mpg) +
  geom_point(mapping = aes(displ, hwy, size = cty))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-7-4.png)<!-- -->

``` r
#year
ggplot(mpg) +
  geom_point(mapping = aes(displ, hwy, color = year))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-7-5.png)<!-- -->

``` r
ggplot(mpg) +
  geom_point(mapping = aes(displ, hwy, size = year))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-7-6.png)<!-- -->

``` r
#combining aes 
ggplot(mpg) +
  geom_point(mapping = aes(displ, hwy, color = year, size = year))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-7-7.png)<!-- -->

``` r
#Discrete/categorical
#model
ggplot(mpg) +
  geom_point(mapping = aes(displ, hwy, color = model))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-8-1.png)<!-- -->

``` r
ggplot(mpg) +
  geom_point(mapping = aes(displ, hwy, size = model))
```

    ## Warning: Using size for a discrete variable is not advised.

![](ch3_fin_files/figure-gfm/unnamed-chunk-8-2.png)<!-- -->

``` r
ggplot(mpg) +
  geom_point(mapping = aes(displ, hwy, shape = model))
```

    ## Warning: The shape palette can deal with a maximum of 6 discrete values because
    ## more than 6 becomes difficult to discriminate; you have 38. Consider
    ## specifying shapes manually if you must have them.

    ## Warning: Removed 199 rows containing missing values (geom_point).

![](ch3_fin_files/figure-gfm/unnamed-chunk-8-3.png)<!-- -->

``` r
#trans
ggplot(mpg) +
  geom_point(mapping = aes(displ, hwy, color = trans))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-8-4.png)<!-- -->

``` r
ggplot(mpg) +
  geom_point(mapping = aes(displ, hwy, size = trans))
```

    ## Warning: Using size for a discrete variable is not advised.

![](ch3_fin_files/figure-gfm/unnamed-chunk-8-5.png)<!-- -->

``` r
ggplot(mpg) +
  geom_point(mapping = aes(displ, hwy, shape = trans))
```

    ## Warning: The shape palette can deal with a maximum of 6 discrete values because
    ## more than 6 becomes difficult to discriminate; you have 10. Consider
    ## specifying shapes manually if you must have them.

    ## Warning: Removed 96 rows containing missing values (geom_point).

![](ch3_fin_files/figure-gfm/unnamed-chunk-8-6.png)<!-- -->

``` r
#drv
ggplot(mpg) +
  geom_point(mapping = aes(displ, hwy, color = drv))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-8-7.png)<!-- -->

``` r
ggplot(mpg) +
  geom_point(mapping = aes(displ, hwy, size = drv))
```

    ## Warning: Using size for a discrete variable is not advised.

![](ch3_fin_files/figure-gfm/unnamed-chunk-8-8.png)<!-- -->

``` r
ggplot(mpg) +
  geom_point(mapping = aes(displ, hwy, shape = drv))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-8-9.png)<!-- -->

``` r
# combining aes
ggplot(mpg) +
  geom_point(mapping = aes(displ, hwy, color = drv, shape = drv))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-8-10.png)<!-- -->

``` r
ggplot(mpg) +
  geom_point(mapping = aes(displ, hwy, color = cyl, alpha = cyl))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-8-11.png)<!-- -->

``` r
ggplot(mpg) + 
  geom_point(mapping = aes(displ, hwy, stroke = displ))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-9-1.png)<!-- -->

``` r
?geom_point
```

    ## starting httpd help server ... done

``` r
#stroke uses different sizes of dots for the categories of the data point

#Sizes defines the size and stroke and allows them to be used by referring to sizes
sizes <- expand.grid(size = (0:3) * 2, stroke = (0:3) * 2)

ggplot(sizes, aes(size, stroke, size = size, stroke = stroke)) + 
  geom_abline(slope = -1, intercept = 6, colour = "white", size = 6) + 
  geom_point(shape = 21, fill = "red") +
  scale_size_identity()
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-9-2.png)<!-- -->

``` r
ggplot(mpg) +
  geom_point(aes(displ, hwy, colour = displ < 5))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-9-3.png)<!-- -->

``` r
#ggplot(mpg) +
  #geom_point(aes(displ, hwy), colour = displ < 5)
#colour needs to be inside the aes

ggplot(mpg) +
  geom_point(aes(displ, hwy, colour = displ < 5), stroke = 5)
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-9-4.png)<!-- -->

``` r
#stroke can be placed outside aes
```

``` r
#3.5 facets examples
ggplot(mpg) + 
  geom_point(aes(x = displ, y = hwy)) + 
  facet_wrap(~ class, nrow = 2)
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-10-1.png)<!-- -->

``` r
#facetwrap variable should be a discrete variable
#below code for facetwrap of 2 variables
ggplot(mpg) + 
  geom_point(aes(x = displ, y = hwy)) + 
  facet_grid(drv ~ cyl)
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-10-2.png)<!-- -->

``` r
#facet wrap for 3 variables
ggplot(mpg) + 
  geom_point(aes(x = displ, y = hwy)) + 
  facet_grid(drv ~ cyl ~ class)
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-10-3.png)<!-- -->

``` r
#facets in one dimension
ggplot(mpg) + 
  geom_point(aes(x = displ, y = hwy)) + 
  facet_grid(. ~ class)
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-10-4.png)<!-- -->

``` r
#exercises 3.5.1.1
#facet wrap on a continous variable
#ggplot(mpg) + 
  #geom_point(aes(x = displ, y = hwy)) + 
  #facet_wrap(~ yeaar, nrow = 2)
#answer 3.5.1: leads to an error

#ex 3.5.1.
ggplot(mpg) + 
  geom_point(aes(x = displ, y = hwy)) + 
  facet_grid(drv ~ cyl)
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-11-1.png)<!-- -->

``` r
#versus
ggplot(mpg) + 
  geom_point(aes(x = drv, y = cyl))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-11-2.png)<!-- -->

``` r
#the facetted plot shows also the amount of data points, the non-facetted one shows only presence in a category. the empty cells mean that there is no data fore/the combination of variables does not exist

#3.5.1.3
ggplot( mpg) + 
  geom_point(mapping = aes(x = displ, y = hwy)) +
  facet_grid(drv ~ .)
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-11-3.png)<!-- -->

``` r
ggplot( mpg) + 
  geom_point(mapping = aes(x = displ, y = hwy)) +
  facet_grid(. ~ cyl)
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-11-4.png)<!-- -->

``` r
#these plots show how to whether to plot the rows or the columns in you facet


#3.5.1.4
ggplot( mpg) + 
  geom_point(mapping = aes(x = displ, y = hwy)) + 
  facet_wrap(~ class, nrow = 2)
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-11-5.png)<!-- -->

``` r
#Orientation: row ~ col
#facets can be used to isolates groups of interest, easy visualize 

#3.5.1.5
ggplot( mpg) + 
  geom_point(mapping = aes(x = displ, y = hwy)) + 
  facet_wrap(~ class, nrow = 1)
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-11-6.png)<!-- -->

``` r
ggplot( mpg) + 
  geom_point(mapping = aes(x = displ, y = hwy)) + 
  facet_wrap(~ class, ncol = 1)
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-11-7.png)<!-- -->

``` r
#using ncol and nrow you can determine the dimensions of the facet 
#facet_wrap wraps a 1d panel in to a 2d panel and used ncol and nrow, so you can customize
#facet_grid forms a matrix of panels 
```

``` r
#3.6 examples
#scatter using geom_point
ggplot(mpg) + 
  geom_point(aes(x = displ, y = hwy))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-12-1.png)<!-- -->

``` r
#line plot using geom_smooth
ggplot(mpg) + 
  geom_smooth(aes(x = displ, y = hwy))
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](ch3_fin_files/figure-gfm/unnamed-chunk-12-2.png)<!-- -->

``` r
#line plot with different linetypes
ggplot(mpg) + 
  geom_smooth(aes(x = displ, y = hwy, linetype = drv))
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](ch3_fin_files/figure-gfm/unnamed-chunk-12-3.png)<!-- -->

``` r
ggplot(mpg) +
  geom_smooth(aes(x = displ, y = hwy))
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](ch3_fin_files/figure-gfm/unnamed-chunk-12-4.png)<!-- -->

``` r
#plots the groups of drv within x and y             
ggplot(mpg) +
  geom_smooth(aes(x = displ, y = hwy, group = drv))
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](ch3_fin_files/figure-gfm/unnamed-chunk-12-5.png)<!-- -->

``` r
#colors different lines    
ggplot(mpg) +
  geom_smooth(
    aes(x = displ, y = hwy, color = drv),
    show.legend = FALSE
  )
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](ch3_fin_files/figure-gfm/unnamed-chunk-12-6.png)<!-- -->

``` r
#plotting both scatter and lines in one figure
ggplot(data = mpg) + 
  geom_point(mapping = aes(x = displ, y = hwy)) +
  geom_smooth(mapping = aes(x = displ, y = hwy))
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](ch3_fin_files/figure-gfm/unnamed-chunk-12-7.png)<!-- -->

``` r
#simpifies the code above
ggplot(mpg, aes(x = displ, y = hwy)) + 
  geom_point() + 
  geom_smooth()
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](ch3_fin_files/figure-gfm/unnamed-chunk-12-8.png)<!-- -->

``` r
#different settings can be used for the type of plotting with plotting the data only once
ggplot(data = mpg, mapping = aes(x = displ, y = hwy)) + 
  geom_point(mapping = aes(color = class)) + 
  geom_smooth()
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](ch3_fin_files/figure-gfm/unnamed-chunk-12-9.png)<!-- -->

``` r
ggplot(data = mpg, mapping = aes(x = displ, y = hwy)) + 
  geom_point(mapping = aes(color = class)) + 
  geom_smooth(data = filter(mpg, class == "subcompact"), se = FALSE)
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](ch3_fin_files/figure-gfm/unnamed-chunk-12-10.png)<!-- -->

``` r
#writing the plot this way allows for customizable settings for each layer
```

``` r
#exercises 3.6
#3.6.1.1
#lineplot
ggplot(mpg) + 
  geom_smooth(aes(displ, hwy))
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](ch3_fin_files/figure-gfm/unnamed-chunk-13-1.png)<!-- -->

``` r
#or
ggplot(mpg) + 
  geom_line(aes(displ, hwy))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-13-2.png)<!-- -->

``` r
#boxplot
ggplot(mpg) + 
  geom_boxplot(aes(displ, hwy))
```

    ## Warning: Continuous x aesthetic -- did you forget aes(group=...)?

![](ch3_fin_files/figure-gfm/unnamed-chunk-13-3.png)<!-- -->

``` r
#histogram
ggplot(mpg,aes(displ)) + 
  geom_histogram()
```

    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](ch3_fin_files/figure-gfm/unnamed-chunk-13-4.png)<!-- -->

``` r
#playing around
ggplot(mpg) + 
  geom_histogram(aes(displ)) +
  geom_histogram(aes(hwy)) +
  facet_grid(~ hwy)
```

    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](ch3_fin_files/figure-gfm/unnamed-chunk-13-5.png)<!-- -->

``` r
ggplot(mpg) + 
  geom_histogram(aes(displ)) +
  geom_histogram(aes(hwy)) +
  facet_grid(~ class)
```

    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.
    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](ch3_fin_files/figure-gfm/unnamed-chunk-13-6.png)<!-- -->

``` r
ggplot(mpg) + 
  geom_histogram(aes(displ)) +
  geom_histogram(aes(hwy)) +
  facet_wrap(~ class, ncol = 4)
```

    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.
    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](ch3_fin_files/figure-gfm/unnamed-chunk-13-7.png)<!-- -->

``` r
#areachart
ggplot(mpg, aes(displ, hwy)) + 
  geom_area()
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-13-8.png)<!-- -->

``` r
#or geom ribbon
ggplot(mpg, aes(displ, hwy, ymin=0 , ymax=50)) + 
  geom_ribbon()
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-13-9.png)<!-- -->

``` r
#for ribbon to look good I probably need to write dat/level to plot

#3.6.1.2
ggplot(mpg, aes(x = displ, y = hwy, color = drv)) + 
  geom_point() + 
  geom_smooth(se = FALSE)
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](ch3_fin_files/figure-gfm/unnamed-chunk-13-10.png)<!-- -->

``` r
#predicted the outcome
ggplot(mpg, aes(x = displ, y = hwy, color = drv)) + 
  geom_point(show.legend = FALSE) + 
  geom_smooth(show.legend = FALSE)
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](ch3_fin_files/figure-gfm/unnamed-chunk-13-11.png)<!-- -->

``` r
#3.6.1.3. show legend is false removes the legend/does not show the legend
#3.6.1.4.the se argument shows the standard error

#3.6.1.5
#they won't look different, below is jsut 2 diff. ways of plotting the same
ggplot(data = mpg, mapping = aes(x = displ, y = hwy)) + 
  geom_point() + 
  geom_smooth()
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](ch3_fin_files/figure-gfm/unnamed-chunk-13-12.png)<!-- -->

``` r
ggplot() + 
  geom_point(data = mpg, mapping = aes(x = displ, y = hwy)) + 
  geom_smooth(data = mpg, mapping = aes(x = displ, y = hwy))
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](ch3_fin_files/figure-gfm/unnamed-chunk-13-13.png)<!-- -->

``` r
#3.6.1.6
#plot 1
ggplot(mpg, aes(displ,hwy)) + 
  geom_point(stroke = 3.5, show.legend = FALSE) + 
  geom_smooth(se = FALSE, show.legend = FALSE)
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](ch3_fin_files/figure-gfm/unnamed-chunk-14-1.png)<!-- -->

``` r
#plot 2
ggplot(mpg, aes(displ,hwy, line = drv)) + 
  geom_point(stroke = 3.5, show.legend = FALSE) + 
  geom_smooth(se = FALSE, show.legend = FALSE)
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](ch3_fin_files/figure-gfm/unnamed-chunk-14-2.png)<!-- -->

``` r
#plot 3
ggplot(mpg, aes(displ,hwy, color = drv)) + 
  geom_point(stroke = 3.5) + 
  geom_smooth(se = FALSE)
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](ch3_fin_files/figure-gfm/unnamed-chunk-14-3.png)<!-- -->

``` r
#plot 4
ggplot(mpg, aes(displ,hwy)) + 
  geom_point(aes(color = drv), stroke = 3.5) + 
  geom_smooth(se = FALSE)
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](ch3_fin_files/figure-gfm/unnamed-chunk-14-4.png)<!-- -->

``` r
#plot 5
ggplot(mpg, aes(displ,hwy, linetype= drv)) + 
  geom_point(aes(color = drv), stroke = 3.5) + 
  geom_smooth(se = FALSE)
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](ch3_fin_files/figure-gfm/unnamed-chunk-14-5.png)<!-- -->

``` r
#plot 6
ggplot(mpg, aes(displ,hwy, fill = drv)) + 
  geom_point(color = "white", size = 3.5, stroke = 3.5)
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-14-6.png)<!-- -->

``` r
ggplot(mpg, aes(displ,hwy, fill = drv)) + 
  geom_point(shape  = 21, color = "white", size = 3.5, stroke = 3.5)
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-14-7.png)<!-- -->

``` r
#without defining shapes drv does not get coloured.
```

``` r
#3.7 examples
diamonds <- ggplot2::diamonds

ggplot(diamonds) +
  geom_bar(mapping = aes(x = cut))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-15-1.png)<!-- -->

``` r
ggplot(data = diamonds) + 
  stat_count(mapping = aes(x = cut))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-15-2.png)<!-- -->

``` r
demo <- tribble(
  ~cut,         ~freq,
  "Fair",       1610,
  "Good",       4906,
  "Very Good",  12082,
  "Premium",    13791,
  "Ideal",      21551
)

ggplot(demo) +
  geom_bar(mapping = aes(cut, freq), stat = "identity")
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-16-1.png)<!-- -->

``` r
ggplot(diamonds) + 
  geom_bar(mapping = aes(cut, stat(prop), group = 1))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-16-2.png)<!-- -->

``` r
ggplot(diamonds) + 
  stat_summary(
    mapping = aes(cut, depth),
    fun.min = min,
    fun.max = max,
    fun = median
  )
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-16-3.png)<!-- -->

``` r
#exercises 3.7

#3.7.1.1
?stat_summary
#pointrange is the default geom
#rewrite
ggplot(diamonds, aes(cut, depth)) + 
  geom_pointrange(aes(ymin = depth, ymax = depth))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-17-1.png)<!-- -->

``` r
#3.7.1.2
#geom_col
ggplot(diamonds, aes(cut, depth)) + 
  geom_col()
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-17-2.png)<!-- -->

``` r
#there are no differences

ggplot(diamonds, aes(cut, depth)) + 
  stat_smooth(aes(depth, ymin = depth, ymax = depth))
```

    ## `geom_smooth()` using method = 'gam' and formula 'y ~ s(x, bs = "cs")'

![](ch3_fin_files/figure-gfm/unnamed-chunk-17-3.png)<!-- -->

``` r
#stat_smooth is controlled bij x or y, and x/y min and max

#3.7.1.5
ggplot(data = diamonds) + 
  geom_bar(mapping = aes(x = cut, y = after_stat(prop)))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-17-4.png)<!-- -->

``` r
ggplot(data = diamonds) + 
  geom_bar(mapping = aes(x = cut, fill = color, y = after_stat(prop)))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-17-5.png)<!-- -->

``` r
#Examples 3.8
ggplot(diamonds) + 
  geom_bar(aes(x = cut, colour = cut))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-18-1.png)<!-- -->

``` r
ggplot(diamonds) + 
  geom_bar(aes(x = cut, fill = cut))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-18-2.png)<!-- -->

``` r
ggplot(data = diamonds) + 
  geom_bar(mapping = aes(x = cut, fill = clarity))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-18-3.png)<!-- -->

``` r
#identity allows for overlapping in the case of bar graphs
ggplot(data = diamonds, mapping = aes(x = cut, fill = clarity)) + 
  geom_bar(alpha = 1/5, position = "identity")
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-18-4.png)<!-- -->

``` r
ggplot(data = diamonds, mapping = aes(x = cut, colour = clarity)) + 
  geom_bar(fill = NA, position = "identity")
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-18-5.png)<!-- -->

``` r
#sets bar to the same height, comparisons for proportions
ggplot(data = diamonds) + 
  geom_bar(mapping = aes(x = cut, fill = clarity), position = "fill")
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-18-6.png)<!-- -->

``` r
#dodge places overlapping objects beside one another
ggplot(data = diamonds) + 
  geom_bar(mapping = aes(x = cut, fill = clarity), position = "dodge")
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-18-7.png)<!-- -->

``` r
#Jitter prevents overplotting of scatterpoints
ggplot(mpg) + 
  geom_point(aes(displ, hwy), position = "jitter")
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-18-8.png)<!-- -->

``` r
#Exercises 3.8
#3.8.1.1
ggplot(mpg, aes(cty, hwy)) + 
  geom_point(position = "jitter")
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-19-1.png)<!-- -->

``` r
ggplot(mpg, aes(cty, hwy)) + 
  geom_point(aes(colour = class), position = "jitter")
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-19-2.png)<!-- -->

``` r
#3.8.1.2.
#alpha/colour/fill/group/shape/size/stroke are the parameters of jitter and x (or) y
#3.8.1.3
ggplot(mpg, aes(cty, hwy)) + 
  geom_count(position = "jitter")
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-19-3.png)<!-- -->

``` r
ggplot(mpg, aes(cty, hwy)) + 
  geom_count(aes(colour = class), position = "jitter")
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-19-4.png)<!-- -->

``` r
#3.8.1.4
ggplot(mpg, aes(cty, hwy))+
  geom_boxplot()
```

    ## Warning: Continuous x aesthetic -- did you forget aes(group=...)?

![](ch3_fin_files/figure-gfm/unnamed-chunk-19-5.png)<!-- -->

``` r
ggplot(mpg, aes(cty, hwy))+
  geom_boxplot(position = "dodge")
```

    ## Warning: Continuous x aesthetic -- did you forget aes(group=...)?

![](ch3_fin_files/figure-gfm/unnamed-chunk-19-6.png)<!-- -->

``` r
ggplot(mpg, aes(cty, hwy))+
  geom_boxplot(position = "identity")
```

    ## Warning: Continuous x aesthetic -- did you forget aes(group=...)?

![](ch3_fin_files/figure-gfm/unnamed-chunk-19-7.png)<!-- -->

``` r
ggplot(mpg, aes(displ, hwy))+
  geom_boxplot()
```

    ## Warning: Continuous x aesthetic -- did you forget aes(group=...)?

![](ch3_fin_files/figure-gfm/unnamed-chunk-19-8.png)<!-- -->

``` r
ggplot(mpg, aes(displ, hwy))+
  geom_boxplot(position = "dodge")
```

    ## Warning: Continuous x aesthetic -- did you forget aes(group=...)?

![](ch3_fin_files/figure-gfm/unnamed-chunk-19-9.png)<!-- -->

``` r
ggplot(mpg, aes(displ, hwy))+
  geom_boxplot(position = "identity")
```

    ## Warning: Continuous x aesthetic -- did you forget aes(group=...)?

![](ch3_fin_files/figure-gfm/unnamed-chunk-19-10.png)<!-- -->

``` r
#no position adjusment or is it dodge
```

``` r
ggplot(mpg, aes(cty, hwy))+
  geom_boxplot(aes(group = class))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-20-1.png)<!-- -->

``` r
ggplot(mpg, aes(cty, hwy))+
  geom_boxplot(aes(group = class), position = "dodge")
```

    ## Warning: position_dodge requires non-overlapping x intervals

![](ch3_fin_files/figure-gfm/unnamed-chunk-20-2.png)<!-- -->

``` r
ggplot(mpg, aes(cty, hwy))+
  geom_boxplot(aes(group = class), position = "identity")
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-20-3.png)<!-- -->

``` r
ggplot(mpg, aes(displ, hwy))+
  geom_boxplot(aes(group = class))
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-20-4.png)<!-- -->

``` r
ggplot(mpg, aes(displ, hwy))+
  geom_boxplot(aes(group = class), position = "dodge")
```

    ## Warning: position_dodge requires non-overlapping x intervals

![](ch3_fin_files/figure-gfm/unnamed-chunk-20-5.png)<!-- -->

``` r
ggplot(mpg, aes(displ, hwy))+
  geom_boxplot(aes(group = class), position = "identity")
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-20-6.png)<!-- -->

``` r
#Examples 3.9
ggplot(data = mpg, mapping = aes(x = class, y = hwy)) + 
  geom_boxplot()
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-21-1.png)<!-- -->

``` r
ggplot(data = mpg, mapping = aes(x = class, y = hwy)) + 
  geom_boxplot() +
  coord_flip()
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-21-2.png)<!-- -->

``` r
nz <- map_data("nz")

ggplot(nz, aes(long, lat, group = group)) +
  geom_polygon(fill = "white", colour = "black")
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-22-1.png)<!-- -->

``` r
ggplot(nz, aes(long, lat, group = group)) +
  geom_polygon(fill = "white", colour = "black") +
  coord_quickmap()
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-22-2.png)<!-- -->

``` r
bar <- ggplot(data = diamonds) + 
  geom_bar(
    mapping = aes(x = cut, fill = cut), 
    show.legend = FALSE,
    width = 1
  ) + 
  theme(aspect.ratio = 1) +
  labs(x = NULL, y = NULL)

bar + coord_flip()
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-23-1.png)<!-- -->

``` r
bar + coord_polar()
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-23-2.png)<!-- -->

``` r
#3.9.1.1
bar2 <- ggplot(data = diamonds) + 
  geom_bar(mapping = aes(x = cut, fill = color, y = after_stat(prop)))

bar2 + coord_flip()
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-24-1.png)<!-- -->

``` r
bar2 + coord_polar()
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-24-2.png)<!-- -->

``` r
#3.9.1.2
#labs() makes labels for graphs/figures

#3.9.1.3
ggplot(nz, aes(long, lat, group = group)) +
  geom_polygon(fill = "white", colour = "black") +
  coord_quickmap()
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-24-3.png)<!-- -->

``` r
ggplot(nz, aes(long, lat, group = group)) +
  geom_polygon(fill = "white", colour = "black") +
  coord_map()
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-24-4.png)<!-- -->

``` r
# the difference is the size of the image/the grid in the background

#3.9.1.4
ggplot(data = mpg, mapping = aes(x = cty, y = hwy)) +
  geom_point() + 
  geom_abline() +
  coord_fixed()
```

![](ch3_fin_files/figure-gfm/unnamed-chunk-24-5.png)<!-- -->

``` r
#without coord_fixed it does not run, coord_fixed is responsible for a fixed scale.
#that it is linear correlated
#geom_abline adds definitions (rules) to the plot
```
