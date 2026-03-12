# Find and visualize peaks in a genomic region

Identifies and visualizes significant peaks within a specified genomic
region, helping to define the boundaries of QTL intervals. This function
finds the maximum association score in the region and determines the
interval boundaries based on specified drops in significance level.

## Usage

``` r
XQTL_zoom(df, chr, start, stop, left_drop = 3, right_drop = 3)
```

## Arguments

- df:

  Data frame with QTL scan results containing columns: chr, pos,
  Wald_log10p

- chr:

  Character string specifying the chromosome to analyze (e.g., "chr2L")

- start:

  Integer specifying the start position in base pairs

- stop:

  Integer specifying the stop position in base pairs

- left_drop:

  Numeric value specifying the drop in -log10(p-value) to the left of
  the peak to define interval start

- right_drop:

  Numeric value specifying the drop in -log10(p-value) to the right of
  the peak to define interval stop

## Value

A list containing: plot (ggplot object showing the region with peak and
boundaries), and interval (data frame with chr, start, stop of the
refined interval)
