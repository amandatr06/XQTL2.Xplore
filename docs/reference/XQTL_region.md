# Plot a genomic region

Creates a line plot showing QTL association statistics across a
specified genomic region. This function generates a simple but effective
visualization of association scores (e.g., -log10(p-values)) with both
points and connecting lines, making it easy to identify peaks and
patterns within a genomic interval.

## Usage

``` r
XQTL_region(df, chr, start, stop, y_var)
```

## Arguments

- df:

  Data frame with QTL scan results containing columns: chr, pos, and the
  variable specified in y_var

- chr:

  Character string specifying the chromosome to analyze (e.g., "chr2L")

- start:

  Integer specifying the start position in base pairs

- stop:

  Integer specifying the stop position in base pairs

- y_var:

  Character string specifying the column name to plot on y-axis (e.g.,
  "Wald_log10p")

## Value

A ggplot object showing association statistics across the genomic region
