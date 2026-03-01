# Convert a correlation data frame to matrix format

Convert a correlation data frame to original matrix format.

## Usage

``` r
as_matrix(x, diagonal)
```

## Arguments

- x:

  A correlation data frame. See
  [`correlate`](https://corrr.tidymodels.org/dev/reference/correlate.md)
  or
  [`as_cordf`](https://corrr.tidymodels.org/dev/reference/as_cordf.md).

- diagonal:

  Value (typically numeric or NA) to set the diagonal to

## Value

Correlation matrix

## Examples

``` r
x <- correlate(mtcars)
#> Correlation computed with
#> • Method: 'pearson'
#> • Missing treated using: 'pairwise.complete.obs'
as_matrix(x)
#>             mpg        cyl       disp         hp        drat
#> mpg          NA -0.8521620 -0.8475514 -0.7761684  0.68117191
#> cyl  -0.8521620         NA  0.9020329  0.8324475 -0.69993811
#> disp -0.8475514  0.9020329         NA  0.7909486 -0.71021393
#> hp   -0.7761684  0.8324475  0.7909486         NA -0.44875912
#> drat  0.6811719 -0.6999381 -0.7102139 -0.4487591          NA
#> wt   -0.8676594  0.7824958  0.8879799  0.6587479 -0.71244065
#> qsec  0.4186840 -0.5912421 -0.4336979 -0.7082234  0.09120476
#> vs    0.6640389 -0.8108118 -0.7104159 -0.7230967  0.44027846
#> am    0.5998324 -0.5226070 -0.5912270 -0.2432043  0.71271113
#> gear  0.4802848 -0.4926866 -0.5555692 -0.1257043  0.69961013
#> carb -0.5509251  0.5269883  0.3949769  0.7498125 -0.09078980
#>              wt        qsec         vs          am       gear
#> mpg  -0.8676594  0.41868403  0.6640389  0.59983243  0.4802848
#> cyl   0.7824958 -0.59124207 -0.8108118 -0.52260705 -0.4926866
#> disp  0.8879799 -0.43369788 -0.7104159 -0.59122704 -0.5555692
#> hp    0.6587479 -0.70822339 -0.7230967 -0.24320426 -0.1257043
#> drat -0.7124406  0.09120476  0.4402785  0.71271113  0.6996101
#> wt           NA -0.17471588 -0.5549157 -0.69249526 -0.5832870
#> qsec -0.1747159          NA  0.7445354 -0.22986086 -0.2126822
#> vs   -0.5549157  0.74453544         NA  0.16834512  0.2060233
#> am   -0.6924953 -0.22986086  0.1683451          NA  0.7940588
#> gear -0.5832870 -0.21268223  0.2060233  0.79405876         NA
#> carb  0.4276059 -0.65624923 -0.5696071  0.05753435  0.2740728
#>             carb
#> mpg  -0.55092507
#> cyl   0.52698829
#> disp  0.39497686
#> hp    0.74981247
#> drat -0.09078980
#> wt    0.42760594
#> qsec -0.65624923
#> vs   -0.56960714
#> am    0.05753435
#> gear  0.27407284
#> carb          NA
```
