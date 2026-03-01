# Changelog

## corrr (development version)

## corrr 0.4.4

CRAN release: 2022-08-16

- Make
  [`colpair_map()`](https://corrr.tidymodels.org/dev/reference/colpair_map.md)
  more robust to input column names, with the exception of “.data” and
  “.env” ([@jameslairdsmith](https://github.com/jameslairdsmith),
  [\#131](https://github.com/tidymodels/corrr/issues/131)).

- [`correlate()`](https://corrr.tidymodels.org/dev/reference/correlate.md)
  now removes non-numeric columns from data frame inputs
  ([@thisisdaryn](https://github.com/thisisdaryn),
  [\#139](https://github.com/tidymodels/corrr/issues/139)).

- [`autoplot.cor_df()`](https://corrr.tidymodels.org/dev/reference/autoplot.cor_df.md)
  method have been added for quick generation of correlation chart.

- [`network_plot()`](https://corrr.tidymodels.org/dev/reference/network_plot.md)
  now allows the user the option to map the color range to the range of
  correlations that are in the input `rdf`
  ([@thisisdaryn](https://github.com/thisisdaryn),
  [\#158](https://github.com/tidymodels/corrr/issues/158)).

## corrr 0.4.3

CRAN release: 2020-11-24

- Fix EOL issues and class attribute
  ([@krlmlr](https://github.com/krlmlr),
  [\#93](https://github.com/tidymodels/corrr/issues/93) and
  [\#90](https://github.com/tidymodels/corrr/issues/90))

- Handle correlation of exactly zero or 1 in
  [`network_plot()`](https://corrr.tidymodels.org/dev/reference/network_plot.md)
  ([@s-scherrer](https://github.com/s-scherrer),
  [\#89](https://github.com/tidymodels/corrr/issues/89))

- Add `.order` argument to
  [`rplot()`](https://corrr.tidymodels.org/dev/reference/rplot.md) with
  options “default” and “alphabet” plus improved documentation
  ([@mattwarkentin](https://github.com/mattwarkentin),
  [\#99](https://github.com/tidymodels/corrr/issues/99) and
  [@thisisdaryn](https://github.com/thisisdaryn),
  [\#114](https://github.com/tidymodels/corrr/issues/114))

- Make
  [`network_plot()`](https://corrr.tidymodels.org/dev/reference/network_plot.md)
  more robust, for example to highly correlated data
  ([@thisisdaryn](https://github.com/thisisdaryn),
  [\#107](https://github.com/tidymodels/corrr/issues/107))

- New
  [`colpair_map()`](https://corrr.tidymodels.org/dev/reference/colpair_map.md)
  allows for column comparisons using the values returned by an
  arbitrary function
  ([@jameslairdsmith](https://github.com/jameslairdsmith),
  [\#94](https://github.com/tidymodels/corrr/issues/94)).

- [`correlate()`](https://corrr.tidymodels.org/dev/reference/correlate.md)
  now works with single-column data.frames and numeric vectors
  ([@antoine-sachet](https://github.com/antoine-sachet),
  [\#122](https://github.com/tidymodels/corrr/issues/122)). Note the
  `diagonal` argument is ignored in these 2 cases.

- [`network_plot()`](https://corrr.tidymodels.org/dev/reference/network_plot.md)
  now works with `cor_df` objects with only 1 or 2 columns
  ([@antoine-sachet](https://github.com/antoine-sachet),
  [\#122](https://github.com/tidymodels/corrr/issues/122))

- The first column of a `cor_df` object is now named “term”. Previously
  it was named “rowname”
  ([@thisisdaryn](https://github.com/thisisdaryn),
  [\#117](https://github.com/tidymodels/corrr/issues/117)).

## corrr 0.4.2

CRAN release: 2020-03-22

- Updates to work with tibble 3.0.0 and dplyr 1.0.0

## corrr 0.4.1

CRAN release: 2020-02-10

- Updates maintainer

## corrr 0.4.0

CRAN release: 2019-07-12

- Adds `remove.dups` argument to
  [`stretch()`](https://corrr.tidymodels.org/dev/reference/stretch.md).
  It removes duplicates with out removing all NAs
  ([\#57](https://github.com/tidymodels/corrr/issues/57))

- Adds [`dice()`](https://corrr.tidymodels.org/dev/reference/dice.md)
  function, wraps `focus(x,..., mirror = TRUE)`
  ([\#64](https://github.com/tidymodels/corrr/issues/64))

- Adds
  [`retract()`](https://corrr.tidymodels.org/dev/reference/retract.md)
  function, opposite of
  [`stretch()`](https://corrr.tidymodels.org/dev/reference/stretch.md)
  ([\#65](https://github.com/tidymodels/corrr/issues/65))

- Improves
  [`correlate()`](https://corrr.tidymodels.org/dev/reference/correlate.md)
  for database backed tables

- Fixes compatibility issues with `dplyr`

## corrr 0.3.2

CRAN release: 2019-04-20

- Improves support for `tbl_sql()` objects

- Switches correlation calculation for `tbl_spark()` tables to
  [`sparklyr::ml_corr()`](https://rdrr.io/pkg/sparklyr/man/ml_corr.html)

- Adds package level doc ([@jsta](https://github.com/jsta),
  [\#66](https://github.com/tidymodels/corrr/issues/66))

- Fixes typo on error message ([@jsta](https://github.com/jsta))

- Removes Database vignette. Plan to re-add later on
  ([\#76](https://github.com/tidymodels/corrr/issues/76))

- Minor updates to Using corrr vignette

## corrr 0.3.1

CRAN release: 2019-03-06

- Fixes test and CRAN issues by removing `Ops.cor_df()`.

- Designates Edgar Ruiz as the new package maintainer

## corrr 0.3.0

CRAN release: 2018-07-31

### Small breaking changes

The `diagonal` argument of `as_matrix` and `as_matrix.cor_df` is now an
optional argument rather than set to `1` by default
[\#52](https://github.com/tidymodels/corrr/issues/52)

### New Functions

- `as_cordf` will coerce lists or matrices into correlation data frames
  if possible.
- `focus_if` enables conditional variable selection.

### New Functionality

- Can use arithmetic operators (e.g., `+` or `-`) with correlation data
  frames.
- Plotting functions (`rplot` and `network_plot`) will attempt to coerce
  objects to a correlation data frame (via `as_cordf`) if needed, making
  it possible to directly use these functions with other
  square-matrix-like objects.
- `repel` option added to `network_plot` (default = `TRUE`).
- `curved` option added to `network_plot` (default = `TRUE`).
- [`correlate()`](https://corrr.tidymodels.org/dev/reference/correlate.md)
  now prints a message about the `method` and `use` parameters. Can be
  silenced with `quiet = TRUE`.
- [`correlate()`](https://corrr.tidymodels.org/dev/reference/correlate.md)
  now supports data frame with a SQL back-end (`tbl_sql`)

### Fixes

- When `legend = TRUE` (now the default setting), `rplot` and
  `network_plot` generate a single, unlabeled legend referring to the
  size of the correlations.

### Other

- [`correlate()`](https://corrr.tidymodels.org/dev/reference/correlate.md)
  is now an S3 method so that it can adapt to `x`’s object type.

- During the development of this version, ggplot v2.2.0 was released.
  Many changes in the plotting functions have been made to handle new
  features in the updated version of ggplot2.

- Improvements to the package folder structure

## corrr 0.2.1

CRAN release: 2016-10-10

### New Functionality

- Can keep leading zeros when using
  [`fashion()`](https://corrr.tidymodels.org/dev/reference/fashion.md)
  with new argument `leading_zeros = TRUE`.
- New optional arguments added to plotting functions,
  [`network_plot()`](https://corrr.tidymodels.org/dev/reference/network_plot.md)
  and [`rplot()`](https://corrr.tidymodels.org/dev/reference/rplot.md):
  - `legend` to display a legend mapping correlations to size and
    colour.
  - `colours` (or `colors`) to change colours in plot.

### Fixes

- [`network_plot()`](https://corrr.tidymodels.org/dev/reference/network_plot.md)
  no longer plots wrong colours if only positive correlations are
  included.
- Colour scheme for
  [`network_plot()`](https://corrr.tidymodels.org/dev/reference/network_plot.md)
  changed to match
  [`rplot()`](https://corrr.tidymodels.org/dev/reference/rplot.md).
- Other bug fixes.

## corrr 0.2.0

CRAN release: 2016-08-11

### New Functions

- [`network_plot()`](https://corrr.tidymodels.org/dev/reference/network_plot.md)
  the correlations.
- [`focus_()`](https://corrr.tidymodels.org/dev/reference/focus.md) for
  standard evaluation version of
  [`focus()`](https://corrr.tidymodels.org/dev/reference/focus.md).

### New Functionality

- [`fashion()`](https://corrr.tidymodels.org/dev/reference/fashion.md)
  will now attempt to work on any object (not just `cor_df`), making it
  useful for printing any data frame, matrix, vector, etc.
- `print_cor` argument added to
  [`rplot()`](https://corrr.tidymodels.org/dev/reference/rplot.md) to
  overlay the correlations as text.

### Other

- `na_omit` argument in
  [`stretch()`](https://corrr.tidymodels.org/dev/reference/stretch.md)
  changed to `na.rm` to match `gather_()`.
- Bug fixes.
- Improvements.

## corrr 0.1.0

CRAN release: 2016-07-08

- First corrr release!
