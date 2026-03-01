# Focus on section of a correlation data frame.

Convenience function to select a set of variables from a correlation
matrix to keep as the columns, and exclude these or all other variables
from the rows. This function will take a
[`correlate`](https://corrr.tidymodels.org/dev/reference/correlate.md)
correlation matrix, and expression(s) suited for dplyr::select(). The
selected variables will remain in the columns, and these, or all other
variables, will be excluded from the rows based on \``same`. For a
complete list of methods for using this function, see
[`select`](https://dplyr.tidyverse.org/reference/select.html).

## Usage

``` r
focus(x, ..., mirror = FALSE)

focus_(x, ..., .dots, mirror)
```

## Arguments

- x:

  cor_df. See
  [`correlate`](https://corrr.tidymodels.org/dev/reference/correlate.md).

- ...:

  One or more unquoted expressions separated by commas. Variable names
  can be used as if they were positions in the data frame, so
  expressions like \`x:y“ can be used to select a range of variables.

- mirror:

  Boolean. Whether to mirror the selected columns in the rows or not.

- .dots:

  Use focus\_ to do standard evaluations. See
  [`select`](https://dplyr.tidyverse.org/reference/select.html).

## Value

A tbl or, if mirror = TRUE, a `cor_df` (see
[`correlate`](https://corrr.tidymodels.org/dev/reference/correlate.md)).

## Examples

``` r
library(dplyr)
x <- correlate(mtcars)
#> Correlation computed with
#> • Method: 'pearson'
#> • Missing treated using: 'pairwise.complete.obs'
focus(x, mpg, cyl) # Focus on correlations of mpg and cyl with all other variables
#> # A tibble: 9 × 3
#>   term     mpg    cyl
#>   <chr>  <dbl>  <dbl>
#> 1 disp  -0.848  0.902
#> 2 hp    -0.776  0.832
#> 3 drat   0.681 -0.700
#> 4 wt    -0.868  0.782
#> 5 qsec   0.419 -0.591
#> 6 vs     0.664 -0.811
#> 7 am     0.600 -0.523
#> 8 gear   0.480 -0.493
#> 9 carb  -0.551  0.527
focus(x, -disp, -mpg, mirror = TRUE) # Remove disp and mpg from columns and rows
#> # A tibble: 9 × 10
#>   term     cyl     hp    drat     wt    qsec     vs      am   gear
#>   <chr>  <dbl>  <dbl>   <dbl>  <dbl>   <dbl>  <dbl>   <dbl>  <dbl>
#> 1 cyl   NA      0.832 -0.700   0.782 -0.591  -0.811 -0.523  -0.493
#> 2 hp     0.832 NA     -0.449   0.659 -0.708  -0.723 -0.243  -0.126
#> 3 drat  -0.700 -0.449 NA      -0.712  0.0912  0.440  0.713   0.700
#> 4 wt     0.782  0.659 -0.712  NA     -0.175  -0.555 -0.692  -0.583
#> 5 qsec  -0.591 -0.708  0.0912 -0.175 NA       0.745 -0.230  -0.213
#> 6 vs    -0.811 -0.723  0.440  -0.555  0.745  NA      0.168   0.206
#> 7 am    -0.523 -0.243  0.713  -0.692 -0.230   0.168 NA       0.794
#> 8 gear  -0.493 -0.126  0.700  -0.583 -0.213   0.206  0.794  NA    
#> 9 carb   0.527  0.750 -0.0908  0.428 -0.656  -0.570  0.0575  0.274
#> # ℹ 1 more variable: carb <dbl>

x <- correlate(iris[-5])
#> Correlation computed with
#> • Method: 'pearson'
#> • Missing treated using: 'pairwise.complete.obs'
focus(x, -matches("Sepal")) # Focus on correlations of non-Sepal
#> # A tibble: 2 × 3
#>   term         Petal.Length Petal.Width
#>   <chr>               <dbl>       <dbl>
#> 1 Sepal.Length        0.872       0.818
#> 2 Sepal.Width        -0.428      -0.366
# variables with Sepal variables.
```
