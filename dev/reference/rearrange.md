# Re-arrange a correlation data frame

Re-arrange a correlation data frame to group highly correlated variables
closer together.

## Usage

``` r
rearrange(x, method = "PC", absolute = TRUE)
```

## Arguments

- x:

  cor_df. See
  [`correlate`](https://corrr.tidymodels.org/dev/reference/correlate.md).

- method:

  String specifying the arrangement (clustering) method. Clustering is
  achieved via
  [`seriate`](https://rdrr.io/pkg/seriation/man/seriate.html), which can
  be consulted for a complete list of clustering methods. Default =
  "PCA".

- absolute:

  Boolean whether absolute values for the correlations should be used
  for clustering.

## Value

cor_df. See
[`correlate`](https://corrr.tidymodels.org/dev/reference/correlate.md).

## Examples

``` r
x <- correlate(mtcars)
#> Correlation computed with
#> • Method: 'pearson'
#> • Missing treated using: 'pairwise.complete.obs'

rearrange(x) # Default settings
#> # A tibble: 11 × 12
#>    term     mpg     vs    drat      am   gear    qsec    carb     hp
#>    <chr>  <dbl>  <dbl>   <dbl>   <dbl>  <dbl>   <dbl>   <dbl>  <dbl>
#>  1 mpg   NA      0.664  0.681   0.600   0.480  0.419  -0.551  -0.776
#>  2 vs     0.664 NA      0.440   0.168   0.206  0.745  -0.570  -0.723
#>  3 drat   0.681  0.440 NA       0.713   0.700  0.0912 -0.0908 -0.449
#>  4 am     0.600  0.168  0.713  NA       0.794 -0.230   0.0575 -0.243
#>  5 gear   0.480  0.206  0.700   0.794  NA     -0.213   0.274  -0.126
#>  6 qsec   0.419  0.745  0.0912 -0.230  -0.213 NA      -0.656  -0.708
#>  7 carb  -0.551 -0.570 -0.0908  0.0575  0.274 -0.656  NA       0.750
#>  8 hp    -0.776 -0.723 -0.449  -0.243  -0.126 -0.708   0.750  NA    
#>  9 wt    -0.868 -0.555 -0.712  -0.692  -0.583 -0.175   0.428   0.659
#> 10 disp  -0.848 -0.710 -0.710  -0.591  -0.556 -0.434   0.395   0.791
#> 11 cyl   -0.852 -0.811 -0.700  -0.523  -0.493 -0.591   0.527   0.832
#> # ℹ 3 more variables: wt <dbl>, disp <dbl>, cyl <dbl>
rearrange(x, method = "HC") # Different seriation method
#> # A tibble: 11 × 12
#>    term      wt    cyl   disp     hp    carb    drat      am   gear
#>    <chr>  <dbl>  <dbl>  <dbl>  <dbl>   <dbl>   <dbl>   <dbl>  <dbl>
#>  1 wt    NA      0.782  0.888  0.659  0.428  -0.712  -0.692  -0.583
#>  2 cyl    0.782 NA      0.902  0.832  0.527  -0.700  -0.523  -0.493
#>  3 disp   0.888  0.902 NA      0.791  0.395  -0.710  -0.591  -0.556
#>  4 hp     0.659  0.832  0.791 NA      0.750  -0.449  -0.243  -0.126
#>  5 carb   0.428  0.527  0.395  0.750 NA      -0.0908  0.0575  0.274
#>  6 drat  -0.712 -0.700 -0.710 -0.449 -0.0908 NA       0.713   0.700
#>  7 am    -0.692 -0.523 -0.591 -0.243  0.0575  0.713  NA       0.794
#>  8 gear  -0.583 -0.493 -0.556 -0.126  0.274   0.700   0.794  NA    
#>  9 qsec  -0.175 -0.591 -0.434 -0.708 -0.656   0.0912 -0.230  -0.213
#> 10 mpg   -0.868 -0.852 -0.848 -0.776 -0.551   0.681   0.600   0.480
#> 11 vs    -0.555 -0.811 -0.710 -0.723 -0.570   0.440   0.168   0.206
#> # ℹ 3 more variables: qsec <dbl>, mpg <dbl>, vs <dbl>
rearrange(x, absolute = FALSE) # Not using absolute values for arranging
#> # A tibble: 11 × 12
#>    term     mpg     vs    drat      am   gear    qsec    carb     hp
#>    <chr>  <dbl>  <dbl>   <dbl>   <dbl>  <dbl>   <dbl>   <dbl>  <dbl>
#>  1 mpg   NA      0.664  0.681   0.600   0.480  0.419  -0.551  -0.776
#>  2 vs     0.664 NA      0.440   0.168   0.206  0.745  -0.570  -0.723
#>  3 drat   0.681  0.440 NA       0.713   0.700  0.0912 -0.0908 -0.449
#>  4 am     0.600  0.168  0.713  NA       0.794 -0.230   0.0575 -0.243
#>  5 gear   0.480  0.206  0.700   0.794  NA     -0.213   0.274  -0.126
#>  6 qsec   0.419  0.745  0.0912 -0.230  -0.213 NA      -0.656  -0.708
#>  7 carb  -0.551 -0.570 -0.0908  0.0575  0.274 -0.656  NA       0.750
#>  8 hp    -0.776 -0.723 -0.449  -0.243  -0.126 -0.708   0.750  NA    
#>  9 wt    -0.868 -0.555 -0.712  -0.692  -0.583 -0.175   0.428   0.659
#> 10 disp  -0.848 -0.710 -0.710  -0.591  -0.556 -0.434   0.395   0.791
#> 11 cyl   -0.852 -0.811 -0.700  -0.523  -0.493 -0.591   0.527   0.832
#> # ℹ 3 more variables: wt <dbl>, disp <dbl>, cyl <dbl>
```
