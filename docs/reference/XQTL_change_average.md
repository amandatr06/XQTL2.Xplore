# Plot average frequency changes or selection coefficients by position

Creates a line plot showing either frequency changes (Δq) or selection
coefficients (s) across a genomic region. This function visualizes how
allele frequencies change between treatment and control conditions, or
the corresponding selection coefficients, for each founder strain across
a specified genomic interval.

## Usage

``` r
XQTL_change_average(
  df,
  chr,
  start,
  stop,
  reference_strain = NULL,
  filter_low_freq_founders = TRUE,
  plotSelection = FALSE
)
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

- reference_strain:

  Optional character string specifying a reference strain to highlight
  in grey

- filter_low_freq_founders:

  Logical, whether to apply transparency to low-frequency founders

- plotSelection:

  Logical, whether to plot selection coefficients (s) instead of
  frequency changes (Δq)

## Value

A ggplot object showing frequency changes or selection coefficients by
position

## Details

This function handles low-frequency founders differently depending on
the plot type:

**For frequency change plots (plotSelection = FALSE):**

- Founders with average frequency \< 2.5% across the interval are
  plotted with reduced transparency (alpha = 0.2)

- low-frequency founders often cannot change in frequency much, so we
  don't want to over-emphasize them

**For selection coefficient plots (plotSelection = TRUE):**

- Founders with average frequency \< 2.5% across the interval are
  completely excluded from the plot

- Founders with any positions having frequency \< 2.5% are plotted with
  reduced transparency (alpha = 0.1)

- This filtering is necessary because the normalization by 2pq can
  produce very large, potentially meaningless values of s when the minor
  allele frequency is small

- Low-alpha lines are plotted in the background to maintain visual
  hierarchy

Selection coefficients are calculated as s = Δq/(2pq), where Δq is the
frequency change and 2pq is the heterozygosity in the control condition
(p=1-q). This normalization can amplify noise when p or q is very small.
