# Apply a function to all pairs of columns in a data frame

`colpair_map()` transforms a data frame by applying a function to each
pair of its columns. The result is a correlation data frame (see
[`correlate`](https://corrr.tidymodels.org/dev/reference/correlate.md)
for details).

## Usage

``` r
colpair_map(.data, .f, ..., .diagonal = NA)
```

## Arguments

- .data:

  A data frame or data frame extension (e.g. a tibble).

- .f:

  A function.

- ...:

  Additional arguments passed on to the mapped function.

- .diagonal:

  Value at which to set the diagonal (defaults to `NA`).

## Value

A correlation data frame (`cor_df`).

## Examples

``` r
## Using `stats::cov` produces a covariance data frame.
colpair_map(mtcars, cov)
#> Warning: There was 1 warning in `dplyr::summarise()`.
#> ℹ In argument: `dplyr::across(...)`.
#> Caused by warning:
#> ! The `...` argument of `across()` is deprecated as of dplyr 1.1.0.
#> Supply arguments directly to `.fns` through an anonymous function
#> instead.
#> 
#>   # Previously
#>   across(a:b, mean, na.rm = TRUE)
#> 
#>   # Now
#>   across(a:b, \(x) mean(x, na.rm = TRUE))
#> ℹ The deprecated feature was likely used in the corrr package.
#>   Please report the issue at
#>   <https://github.com/tidymodels/corrr/issues>.
#> # A tibble: 11 × 12
#>    term      mpg     cyl   disp      hp     drat      wt     qsec
#>    <chr>   <dbl>   <dbl>  <dbl>   <dbl>    <dbl>   <dbl>    <dbl>
#>  1 mpg     NA     -9.17  -633.  -321.     2.20    -5.12    4.51  
#>  2 cyl     -9.17  NA      200.   102.    -0.668    1.37   -1.89  
#>  3 disp  -633.   200.      NA   6721.   -47.1    108.    -96.1   
#>  4 hp    -321.   102.    6721.    NA    -16.5     44.2   -86.8   
#>  5 drat     2.20  -0.668  -47.1  -16.5   NA       -0.373   0.0871
#>  6 wt      -5.12   1.37   108.    44.2   -0.373   NA      -0.305 
#>  7 qsec     4.51  -1.89   -96.1  -86.8    0.0871  -0.305  NA     
#>  8 vs       2.02  -0.730  -44.4  -25.0    0.119   -0.274   0.671 
#>  9 am       1.80  -0.466  -36.6   -8.32   0.190   -0.338  -0.205 
#> 10 gear     2.14  -0.649  -50.8   -6.36   0.276   -0.421  -0.280 
#> 11 carb    -5.36   1.52    79.1   83.0   -0.0784   0.676  -1.89  
#> # ℹ 4 more variables: vs <dbl>, am <dbl>, gear <dbl>, carb <dbl>

## Function to get the p-value from a t-test:
calc_p_value <- function(vec_a, vec_b) {
  t.test(vec_a, vec_b)$p.value
}

colpair_map(mtcars, calc_p_value)
#> # A tibble: 11 × 12
#>    term        mpg       cyl      disp        hp      drat        wt
#>    <chr>     <dbl>     <dbl>     <dbl>     <dbl>     <dbl>     <dbl>
#>  1 mpg   NA         9.51e-15  7.98e-11  1.03e-11  3.16e-16  1.03e-16
#>  2 cyl    9.51e-15 NA         1.77e-11  8.32e-13  2.28e- 9  9.12e-11
#>  3 disp   7.98e-11  1.77e-11 NA         1.55e- 3  1.35e-11  1.29e-11
#>  4 hp     1.03e-11  8.32e-13  1.55e- 3 NA         5.28e-13  4.92e-13
#>  5 drat   3.16e-16  2.28e- 9  1.35e-11  5.28e-13 NA         6.02e- 2
#>  6 wt     1.03e-16  9.12e-11  1.29e-11  4.92e-13  6.02e- 2 NA       
#>  7 qsec   5.11e- 2  3.73e-35  6.34e-11  7.24e-12  5.91e-33  7.27e-39
#>  8 vs     2.24e-18  3.50e-19  9.62e-12  3.01e-13  2.43e-33  1.33e-18
#>  9 am     2.15e-18  3.07e-19  9.59e-12  3.00e-13  1.14e-33  9.09e-19
#> 10 gear   3.08e-16  5.64e- 9  1.36e-11  5.36e-13  5.75e- 1  3.41e- 2
#> 11 carb   1.68e-17  5.61e-11  1.24e-11  4.55e-13  1.30e- 2  2.31e- 1
#> # ℹ 5 more variables: qsec <dbl>, vs <dbl>, am <dbl>, gear <dbl>,
#> #   carb <dbl>
```
