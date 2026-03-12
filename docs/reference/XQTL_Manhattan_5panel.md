# XQTL Manhattan 5-panel Plot

Creates a multi-panel Manhattan plot showing each chromosome separately
in its own facet. This function generates five individual Manhattan
plots (one per chromosome) arranged vertically, making it easier to
examine detailed patterns within each chromosome. Each panel shows the
same association statistics but with independent scaling for better
visualization of chromosome-specific features. If multiple_traits_column
is provided, points are colored by this column using a standard 8-color
palette and a legend is added. The function uses tidyverse/dplyr idioms
and tidy evaluation throughout.

## Usage

``` r
XQTL_Manhattan_5panel(df, cM = FALSE, multiple_traits_column = NULL)
```

## Arguments

- df:

  A data frame containing QTL scan results with columns: chr, pos,
  Wald_log10p, and optionally cM

- cM:

  Logical, whether to use genetic distance (cM) instead of physical
  distance (Mb) for x-axis

- multiple_traits_column:

  Optional. Character string specifying the column in df that represents
  different studies/traits. If provided, points will be colored by this
  column using a standard 8-color palette and a legend will be added.

## Value

A ggplot object with five faceted Manhattan plots, one per chromosome
