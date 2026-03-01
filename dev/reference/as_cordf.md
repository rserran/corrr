# Coerce lists and matrices to correlation data frames

A wrapper function to coerce objects in a valid format (such as
correlation matrices created using the base function,
[`cor`](https://rdrr.io/r/stats/cor.html)) into a correlation data
frame.

## Usage

``` r
as_cordf(x, diagonal = NA)
```

## Arguments

- x:

  A list, data frame or matrix that can be coerced into a correlation
  data frame.

- diagonal:

  Value (typically numeric or NA) to set the diagonal to

## Value

A correlation data frame

## Examples

``` r
x <- cor(mtcars)
as_cordf(x)
#> # A tibble: 11 × 12
#>    term     mpg    cyl   disp     hp    drat     wt    qsec     vs
#>    <chr>  <dbl>  <dbl>  <dbl>  <dbl>   <dbl>  <dbl>   <dbl>  <dbl>
#>  1 mpg   NA     -0.852 -0.848 -0.776  0.681  -0.868  0.419   0.664
#>  2 cyl   -0.852 NA      0.902  0.832 -0.700   0.782 -0.591  -0.811
#>  3 disp  -0.848  0.902 NA      0.791 -0.710   0.888 -0.434  -0.710
#>  4 hp    -0.776  0.832  0.791 NA     -0.449   0.659 -0.708  -0.723
#>  5 drat   0.681 -0.700 -0.710 -0.449 NA      -0.712  0.0912  0.440
#>  6 wt    -0.868  0.782  0.888  0.659 -0.712  NA     -0.175  -0.555
#>  7 qsec   0.419 -0.591 -0.434 -0.708  0.0912 -0.175 NA       0.745
#>  8 vs     0.664 -0.811 -0.710 -0.723  0.440  -0.555  0.745  NA    
#>  9 am     0.600 -0.523 -0.591 -0.243  0.713  -0.692 -0.230   0.168
#> 10 gear   0.480 -0.493 -0.556 -0.126  0.700  -0.583 -0.213   0.206
#> 11 carb  -0.551  0.527  0.395  0.750 -0.0908  0.428 -0.656  -0.570
#> # ℹ 3 more variables: am <dbl>, gear <dbl>, carb <dbl>
as_cordf(x, diagonal = 1)
#> # A tibble: 11 × 12
#>    term     mpg    cyl   disp     hp    drat     wt    qsec     vs
#>    <chr>  <dbl>  <dbl>  <dbl>  <dbl>   <dbl>  <dbl>   <dbl>  <dbl>
#>  1 mpg    1     -0.852 -0.848 -0.776  0.681  -0.868  0.419   0.664
#>  2 cyl   -0.852  1      0.902  0.832 -0.700   0.782 -0.591  -0.811
#>  3 disp  -0.848  0.902  1      0.791 -0.710   0.888 -0.434  -0.710
#>  4 hp    -0.776  0.832  0.791  1     -0.449   0.659 -0.708  -0.723
#>  5 drat   0.681 -0.700 -0.710 -0.449  1      -0.712  0.0912  0.440
#>  6 wt    -0.868  0.782  0.888  0.659 -0.712   1     -0.175  -0.555
#>  7 qsec   0.419 -0.591 -0.434 -0.708  0.0912 -0.175  1       0.745
#>  8 vs     0.664 -0.811 -0.710 -0.723  0.440  -0.555  0.745   1    
#>  9 am     0.600 -0.523 -0.591 -0.243  0.713  -0.692 -0.230   0.168
#> 10 gear   0.480 -0.493 -0.556 -0.126  0.700  -0.583 -0.213   0.206
#> 11 carb  -0.551  0.527  0.395  0.750 -0.0908  0.428 -0.656  -0.570
#> # ℹ 3 more variables: am <dbl>, gear <dbl>, carb <dbl>
```
