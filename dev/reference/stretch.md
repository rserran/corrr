# Stretch correlation data frame into long format.

`stretch` is a specified implementation of tidyr::gather() to be applied
to a correlation data frame. It will gather the columns into a
long-format data frame. The term column is handled automatically.

## Usage

``` r
stretch(x, na.rm = FALSE, remove.dups = FALSE)
```

## Arguments

- x:

  cor_df. See
  [`correlate`](https://corrr.tidymodels.org/dev/reference/correlate.md).

- na.rm:

  Boolean. Whether rows with an NA correlation (originally the matrix
  diagonal) should be dropped? Will automatically be set to TRUE if
  mirror is FALSE.

- remove.dups:

  Removes duplicate entries, without removing all NAs

## Value

tbl with three columns (x and y variables, and their correlation)

## Examples

``` r
x <- correlate(mtcars)
#> Correlation computed with
#> • Method: 'pearson'
#> • Missing treated using: 'pairwise.complete.obs'
stretch(x) # Convert all to long format
#> # A tibble: 121 × 3
#>    x     y          r
#>    <chr> <chr>  <dbl>
#>  1 mpg   mpg   NA    
#>  2 mpg   cyl   -0.852
#>  3 mpg   disp  -0.848
#>  4 mpg   hp    -0.776
#>  5 mpg   drat   0.681
#>  6 mpg   wt    -0.868
#>  7 mpg   qsec   0.419
#>  8 mpg   vs     0.664
#>  9 mpg   am     0.600
#> 10 mpg   gear   0.480
#> # ℹ 111 more rows
stretch(x, na.rm = TRUE) # omit NAs (diagonal in this case)
#> # A tibble: 110 × 3
#>    x     y          r
#>    <chr> <chr>  <dbl>
#>  1 mpg   cyl   -0.852
#>  2 mpg   disp  -0.848
#>  3 mpg   hp    -0.776
#>  4 mpg   drat   0.681
#>  5 mpg   wt    -0.868
#>  6 mpg   qsec   0.419
#>  7 mpg   vs     0.664
#>  8 mpg   am     0.600
#>  9 mpg   gear   0.480
#> 10 mpg   carb  -0.551
#> # ℹ 100 more rows

x <- shave(x) # use shave to set upper triangle to NA and then...
stretch(x, na.rm = TRUE) # omit all NAs, therefore keeping each
#> # A tibble: 55 × 3
#>    x     y          r
#>    <chr> <chr>  <dbl>
#>  1 mpg   cyl   -0.852
#>  2 mpg   disp  -0.848
#>  3 mpg   hp    -0.776
#>  4 mpg   drat   0.681
#>  5 mpg   wt    -0.868
#>  6 mpg   qsec   0.419
#>  7 mpg   vs     0.664
#>  8 mpg   am     0.600
#>  9 mpg   gear   0.480
#> 10 mpg   carb  -0.551
#> # ℹ 45 more rows
# correlation only once.
```
