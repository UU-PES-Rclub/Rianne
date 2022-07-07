Challenge 4
================

\#Libraries

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
library(magrittr)
```

    ## 
    ## Attaching package: 'magrittr'

    ## The following object is masked from 'package:purrr':
    ## 
    ##     set_names

    ## The following object is masked from 'package:tidyr':
    ## 
    ##     extract

``` r
library(readxl)
```

\#Loading documents

``` r
clusters <- read_excel("clusters.xlsx")
dim(clusters)
```

    ## [1] 1535    2

``` r
df <- read.table("SUBSET.Hist.Series_TMMnorm_Gmax275.txt", header=T,sep="\t")
dim(df)
```

    ## [1] 5155   19

\#Subsetting

``` r
cl_subset <- df %>%
  filter(df$Glyma.ID %in% clusters$Glyma.ID)
uniq <- unique(clusters$Glyma.ID)

merged <- merge(df, clusters)
unique_m1 <- unique(merged$Glyma.ID)
#merged_2 <- merge(clusters, df)
#either merge yields the same outcome only the place of the addition of the column is different
cl_A <- merged %>%
  filter(Cluster == "A")
cl_B <- merged %>%
  filter(Cluster == "B")
cl_C <- merged %>%
  filter(Cluster == "C")
cl_D <- merged %>%
  filter(Cluster == "D")
```

# 
