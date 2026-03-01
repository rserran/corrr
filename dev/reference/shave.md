# Shave off upper/lower triangle.

Convert the upper or lower triangle of a correlation data frame (cor_df)
to missing values.

## Usage

``` r
shave(x, upper = TRUE)
```

## Arguments

- x:

  cor_df. See
  [`correlate`](https://corrr.tidymodels.org/dev/reference/correlate.md).

- upper:

  Boolean. If TRUE, set upper triangle to NA; lower triangle if FALSE.

## Value

cor_df. See
[`correlate`](https://corrr.tidymodels.org/dev/reference/correlate.md).

## Examples

``` r
x <- correlate(mtcars)
#> Correlation computed with
#> • Method: 'pearson'
#> • Missing treated using: 'pairwise.complete.obs'
shave(x) # Default; shave upper triangle
#> # A tibble: 11 × 12
#>    term     mpg    cyl   disp     hp    drat     wt   qsec     vs
#>    <chr>  <dbl>  <dbl>  <dbl>  <dbl>   <dbl>  <dbl>  <dbl>  <dbl>
#>  1 mpg   NA     NA     NA     NA     NA      NA     NA     NA    
#>  2 cyl   -0.852 NA     NA     NA     NA      NA     NA     NA    
#>  3 disp  -0.848  0.902 NA     NA     NA      NA     NA     NA    
#>  4 hp    -0.776  0.832  0.791 NA     NA      NA     NA     NA    
#>  5 drat   0.681 -0.700 -0.710 -0.449 NA      NA     NA     NA    
#>  6 wt    -0.868  0.782  0.888  0.659 -0.712  NA     NA     NA    
#>  7 qsec   0.419 -0.591 -0.434 -0.708  0.0912 -0.175 NA     NA    
#>  8 vs     0.664 -0.811 -0.710 -0.723  0.440  -0.555  0.745 NA    
#>  9 am     0.600 -0.523 -0.591 -0.243  0.713  -0.692 -0.230  0.168
#> 10 gear   0.480 -0.493 -0.556 -0.126  0.700  -0.583 -0.213  0.206
#> 11 carb  -0.551  0.527  0.395  0.750 -0.0908  0.428 -0.656 -0.570
#> # ℹ 3 more variables: am <dbl>, gear <dbl>, carb <dbl>
shave(x, upper = FALSE) # shave lower triangle
#> # A tibble: 11 × 12
#>    term    mpg    cyl   disp     hp   drat     wt    qsec     vs     am
#>    <chr> <dbl>  <dbl>  <dbl>  <dbl>  <dbl>  <dbl>   <dbl>  <dbl>  <dbl>
#>  1 mpg      NA -0.852 -0.848 -0.776  0.681 -0.868  0.419   0.664  0.600
#>  2 cyl      NA NA      0.902  0.832 -0.700  0.782 -0.591  -0.811 -0.523
#>  3 disp     NA NA     NA      0.791 -0.710  0.888 -0.434  -0.710 -0.591
#>  4 hp       NA NA     NA     NA     -0.449  0.659 -0.708  -0.723 -0.243
#>  5 drat     NA NA     NA     NA     NA     -0.712  0.0912  0.440  0.713
#>  6 wt       NA NA     NA     NA     NA     NA     -0.175  -0.555 -0.692
#>  7 qsec     NA NA     NA     NA     NA     NA     NA       0.745 -0.230
#>  8 vs       NA NA     NA     NA     NA     NA     NA      NA      0.168
#>  9 am       NA NA     NA     NA     NA     NA     NA      NA     NA    
#> 10 gear     NA NA     NA     NA     NA     NA     NA      NA     NA    
#> 11 carb     NA NA     NA     NA     NA     NA     NA      NA     NA    
#> # ℹ 2 more variables: gear <dbl>, carb <dbl>
```
