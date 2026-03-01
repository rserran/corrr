# Add a first column to a data.frame

Add a first column to a data.frame. This is most commonly used to append
a term column to create a cor_df.

## Usage

``` r
first_col(df, ..., var = "term")
```

## Arguments

- df:

  Data frame

- ...:

  Values to go into the column

- var:

  Label for the column, with the default "term"

## Examples

``` r
first_col(mtcars, 1:nrow(mtcars))
#> # A tibble: 32 × 12
#>     term   mpg   cyl  disp    hp  drat    wt  qsec    vs    am  gear
#>    <int> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl> <dbl>
#>  1     1  21       6  160    110  3.9   2.62  16.5     0     1     4
#>  2     2  21       6  160    110  3.9   2.88  17.0     0     1     4
#>  3     3  22.8     4  108     93  3.85  2.32  18.6     1     1     4
#>  4     4  21.4     6  258    110  3.08  3.22  19.4     1     0     3
#>  5     5  18.7     8  360    175  3.15  3.44  17.0     0     0     3
#>  6     6  18.1     6  225    105  2.76  3.46  20.2     1     0     3
#>  7     7  14.3     8  360    245  3.21  3.57  15.8     0     0     3
#>  8     8  24.4     4  147.    62  3.69  3.19  20       1     0     4
#>  9     9  22.8     4  141.    95  3.92  3.15  22.9     1     0     4
#> 10    10  19.2     6  168.   123  3.92  3.44  18.3     1     0     4
#> # ℹ 22 more rows
#> # ℹ 1 more variable: carb <dbl>
```
