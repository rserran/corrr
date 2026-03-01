# Returns a correlation table with the selected fields only

Returns a correlation table with the selected fields only

## Usage

``` r
dice(x, ...)
```

## Arguments

- x:

  A correlation table, class cor_df

- ...:

  A list of variables in the correlation table

## Examples

``` r
dice(correlate(mtcars), mpg, wt, am)
#> Correlation computed with
#> • Method: 'pearson'
#> • Missing treated using: 'pairwise.complete.obs'
#> # A tibble: 3 × 4
#>   term     mpg     wt     am
#>   <chr>  <dbl>  <dbl>  <dbl>
#> 1 mpg   NA     -0.868  0.600
#> 2 wt    -0.868 NA     -0.692
#> 3 am     0.600 -0.692 NA    
```
