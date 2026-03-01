# Correlation Data Frame

An implementation of stats::cor(), which returns a correlation data
frame rather than a matrix. See details below. Additional adjustment
include the use of pairwise deletion by default.

## Usage

``` r
correlate(
  x,
  y = NULL,
  use = "pairwise.complete.obs",
  method = "pearson",
  diagonal = NA,
  quiet = FALSE
)
```

## Arguments

- x:

  a numeric vector, matrix or data frame.

- y:

  `NULL` (default) or a vector, matrix or data frame with compatible
  dimensions to `x`. The default is equivalent to `y = x` (but more
  efficient).

- use:

  an optional character string giving a method for computing covariances
  in the presence of missing values. This must be (an abbreviation of)
  one of the strings `"everything"`, `"all.obs"`, `"complete.obs"`,
  `"na.or.complete"`, or `"pairwise.complete.obs"`.

- method:

  a character string indicating which correlation coefficient (or
  covariance) is to be computed. One of `"pearson"` (default),
  `"kendall"`, or `"spearman"`: can be abbreviated.

- diagonal:

  Value (typically numeric or NA) to set the diagonal to

- quiet:

  Set as TRUE to suppress message about `method` and `use` parameters.

## Value

A correlation data frame `cor_df`

## Details

This function returns a correlation matrix as a correlation data frame
in the following format:

- A tibble (see
  [`tibble`](https://tibble.tidyverse.org/reference/tibble.html))

- An additional class, "cor_df"

- A "term" column

- Standardized variances (the matrix diagonal) set to missing values by
  default (`NA`) so they can be ignored in calculations.

The `use` argument and its possible values are inherited from
[`stats::cor()`](https://rdrr.io/r/stats/cor.html):

- "everything": NAs will propagate conceptually, i.e. a resulting value
  will be NA whenever one of its contributing observations is NA

- "all.obs": the presence of missing observations will produce an error

- "complete.obs": correlations will be computed from complete
  observations, with an error being raised if there are no complete
  cases.

- "na.or.complete": correlations will be computed from complete
  observations, returning an NA if there are no complete cases.

- "pairwise.complete.obs": the correlation between each pair of
  variables is computed using all complete pairs of those particular
  variables.

As of version 0.4.3, the first column of a `cor_df` object is named
"term". In previous versions this first column was named "rowname".

There is a
[`ggplot2::autoplot()`](https://ggplot2.tidyverse.org/reference/autoplot.html)
method for quickly visualizing the correlation matrix, for more
information see
[`autoplot.cor_df()`](https://corrr.tidymodels.org/dev/reference/autoplot.cor_df.md).

## Examples

``` r
if (FALSE) { # \dontrun{
correlate(iris)
} # }

correlate(iris[-5])
#> Correlation computed with
#> • Method: 'pearson'
#> • Missing treated using: 'pairwise.complete.obs'
#> # A tibble: 4 × 5
#>   term         Sepal.Length Sepal.Width Petal.Length Petal.Width
#>   <chr>               <dbl>       <dbl>        <dbl>       <dbl>
#> 1 Sepal.Length       NA          -0.118        0.872       0.818
#> 2 Sepal.Width        -0.118      NA           -0.428      -0.366
#> 3 Petal.Length        0.872      -0.428       NA           0.963
#> 4 Petal.Width         0.818      -0.366        0.963      NA    

correlate(mtcars)
#> Correlation computed with
#> • Method: 'pearson'
#> • Missing treated using: 'pairwise.complete.obs'
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
if (FALSE) { # \dontrun{

# Also supports DB backend and collects results into memory

library(sparklyr)
sc <- spark_connect(master = "local")
mtcars_tbl <- copy_to(sc, mtcars)
mtcars_tbl %>%
  correlate(use = "pairwise.complete.obs", method = "spearman")
spark_disconnect(sc)
} # }
```
