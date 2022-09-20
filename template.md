Data Import
================

``` r
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────── tidyverse 1.3.2 ──
    ## ✔ ggplot2 3.3.6      ✔ purrr   0.3.4 
    ## ✔ tibble  3.1.8      ✔ dplyr   1.0.10
    ## ✔ tidyr   1.2.1      ✔ stringr 1.4.1 
    ## ✔ readr   2.1.2      ✔ forcats 0.5.2 
    ## ── Conflicts ────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

## Data Import: CSVs

Let’s import data using the `readr` package.

``` r
litters_df = read_csv("data/FAS_litters.csv")
```

    ## New names:
    ## Rows: 51 Columns: 8
    ## ── Column specification
    ## ──────────────────────────────────────────────────────── Delimiter: "," chr
    ## (8): this is group, this is litter, ...3, ...4, ...5, ...6, ...7, ...8
    ## ℹ Use `spec()` to retrieve the full column specification for this data. ℹ
    ## Specify the column types or set `show_col_types = FALSE` to quiet this message.
    ## • `` -> `...3`
    ## • `` -> `...4`
    ## • `` -> `...5`
    ## • `` -> `...6`
    ## • `` -> `...7`
    ## • `` -> `...8`

``` r
litters_df = janitor::clean_names(litters_df)
```

Look at the data

``` r
litters_df
```

    ## # A tibble: 51 × 8
    ##    this_is_group this_is_litter             x3     x4    x5    x6    x7    x8   
    ##    <chr>         <chr>                      <chr>  <chr> <chr> <chr> <chr> <chr>
    ##  1 <NA>          (my favorite color is red) <NA>   <NA>  <NA>  <NA>  <NA>  <NA> 
    ##  2 Group         Litter Number              GD0 w… GD18… GD o… Pups… Pups… Pups…
    ##  3 Con7          #85                        999    34.7  20    3     4     3    
    ##  4 Con7          #1/2/95/2                  999    42    19    8     0     7    
    ##  5 Con7          #5/5/3/83/3-3              26     88    19    6     0     5    
    ##  6 Con7          #5/4/2/95/2                28.5   44.1  19    5     1     4    
    ##  7 Con7          #4/2/95/3-3                <NA>   <NA>  20    6     0     6    
    ##  8 Con7          #2/2/95/3-2                <NA>   <NA>  20    6     0     4    
    ##  9 Con7          #1/5/3/83/3-3/2            <NA>   <NA>  20    9     0     9    
    ## 10 Con8          #3/83/3-3                  <NA>   <NA>  20    9     1     8    
    ## # … with 41 more rows

``` r
head(litters_df)
```

    ## # A tibble: 6 × 8
    ##   this_is_group this_is_litter             x3      x4    x5    x6    x7    x8   
    ##   <chr>         <chr>                      <chr>   <chr> <chr> <chr> <chr> <chr>
    ## 1 <NA>          (my favorite color is red) <NA>    <NA>  <NA>  <NA>  <NA>  <NA> 
    ## 2 Group         Litter Number              GD0 we… GD18… GD o… Pups… Pups… Pups…
    ## 3 Con7          #85                        999     34.7  20    3     4     3    
    ## 4 Con7          #1/2/95/2                  999     42    19    8     0     7    
    ## 5 Con7          #5/5/3/83/3-3              26      88    19    6     0     5    
    ## 6 Con7          #5/4/2/95/2                28.5    44.1  19    5     1     4

``` r
tail(litters_df)
```

    ## # A tibble: 6 × 8
    ##   this_is_group this_is_litter x3    x4    x5    x6    x7    x8   
    ##   <chr>         <chr>          <chr> <chr> <chr> <chr> <chr> <chr>
    ## 1 Low8          #79            25.4  43.8  19    8     0     7    
    ## 2 Low8          #100           20    39.2  20    8     0     7    
    ## 3 Low8          #4/84          21.8  35.2  20    4     0     4    
    ## 4 Low8          #108           25.6  47.5  20    8     0     7    
    ## 5 Low8          #99            23.5  39    20    6     0     5    
    ## 6 Low8          #110           25.5  42.7  20    7     0     6

``` r
view(litters_df)
```

``` r
skimr::skim(litters_df)
```

|                                                  |            |
|:-------------------------------------------------|:-----------|
| Name                                             | litters_df |
| Number of rows                                   | 51         |
| Number of columns                                | 8          |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_   |            |
| Column type frequency:                           |            |
| character                                        | 8          |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |            |
| Group variables                                  | None       |

Data summary

**Variable type: character**

| skim_variable  | n_missing | complete_rate | min | max | empty | n_unique | whitespace |
|:---------------|----------:|--------------:|----:|----:|------:|---------:|-----------:|
| this_is_group  |         1 |          0.98 |   4 |   5 |     0 |        7 |          0 |
| this_is_litter |         0 |          1.00 |   3 |  26 |     0 |       51 |          0 |
| x3             |        16 |          0.69 |   2 |  10 |     0 |       25 |          0 |
| x4             |        18 |          0.65 |   2 |  11 |     0 |       31 |          0 |
| x5             |         1 |          0.98 |   2 |  11 |     0 |        3 |          0 |
| x6             |         1 |          0.98 |   1 |  15 |     0 |        9 |          0 |
| x7             |         1 |          0.98 |   1 |  17 |     0 |        5 |          0 |
| x8             |         1 |          0.98 |   1 |  12 |     0 |       10 |          0 |

`read_csv` options..

``` r
read_csv("data/FAS_litters.csv", na = c("","NA",999,88, skip=2)
```

## Other File Formats
