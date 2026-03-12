# XQTL Manhattan Plot

Creates a Manhattan plot for XQTL analysis results, showing association
statistics across the genome. This function generates a traditional
Manhattan plot with chromosomes arranged along the x-axis and
-log10(p-values) on the y-axis. It supports both physical (Mb) and
genetic (cM) distance scales, and includes multiple color schemes for
different institutions.

## Usage

``` r
XQTL_Manhattan(df, cM = FALSE, color_scheme = "KU")
```

## Arguments

- df:

  A data frame containing QTL scan results with columns: chr, pos,
  Wald_log10p, and optionally cM

- cM:

  Logical, whether to use genetic distance (cM) instead of physical
  distance (Mb) for x-axis

- color_scheme:

  Character string specifying the color scheme. Options include: "KU",
  "UCI", "Stanford", "Harvard", "MIT", "Berkeley", "McMaster", "McGill",
  "Oxford", "Cambridge", "NineInchNails"

## Value

A ggplot object showing the Manhattan plot with association statistics
