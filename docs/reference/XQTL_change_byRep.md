# Plot frequency changes by replicate

Creates a multi-panel plot showing frequency changes across replicates
for the top 4 founders. This function visualizes how allele frequencies
change between treatment and control conditions across different
experimental replicates, helping to assess reproducibility and
founder-specific responses to selection.

## Usage

``` r
XQTL_change_byRep(df, chr, start, stop)
```

## Arguments

- df:

  Data frame containing frequency data with columns: chr, pos, founder,
  TRT, freq, REP

- chr:

  Character string specifying the chromosome to analyze (e.g., "chr2L")

- start:

  Integer specifying the start position in base pairs

- stop:

  Integer specifying the stop position in base pairs

## Value

A ggplot object with 4 panels (one per founder) showing frequency
changes by replicate
