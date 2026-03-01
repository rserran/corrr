# Number of pairwise complete cases.

Compute the number of complete cases in a pairwise fashion for `x` (and
`y`).

## Usage

``` r
pair_n(x, y = NULL)
```

## Arguments

- x:

  a numeric vector, matrix or data frame.

- y:

  `NULL` (default) or a vector, matrix or data frame with compatible
  dimensions to `x`. The default is equivalent to `y = x` (but more
  efficient).

## Value

Matrix of pairwise sample sizes (number of complete cases).

## Examples

``` r
pair_n(mtcars)
#>      mpg cyl disp hp drat wt qsec vs am gear carb
#> mpg   32  32   32 32   32 32   32 32 32   32   32
#> cyl   32  32   32 32   32 32   32 32 32   32   32
#> disp  32  32   32 32   32 32   32 32 32   32   32
#> hp    32  32   32 32   32 32   32 32 32   32   32
#> drat  32  32   32 32   32 32   32 32 32   32   32
#> wt    32  32   32 32   32 32   32 32 32   32   32
#> qsec  32  32   32 32   32 32   32 32 32   32   32
#> vs    32  32   32 32   32 32   32 32 32   32   32
#> am    32  32   32 32   32 32   32 32 32   32   32
#> gear  32  32   32 32   32 32   32 32 32   32   32
#> carb  32  32   32 32   32 32   32 32 32   32   32
#> attr(,"class")
#> [1] "n_mat"  "matrix"
```
