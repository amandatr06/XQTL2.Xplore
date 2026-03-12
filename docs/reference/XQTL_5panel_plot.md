# Create a 5-panel XQTL plot with shared X-axis and combined legend using patchwork only

Generates a comprehensive 5-panel visualization combining QTL
association results, frequency changes, structural variants, and gene
annotations for a genomic region. This function creates a
publication-ready figure with aligned X-axes across all panels and a
manually constructed combined legend showing founder colors and
structural variant types.

## Usage

``` r
XQTL_5panel_plot(
  df1,
  df2,
  dm6_variants,
  dm6_genes,
  chr,
  start,
  stop,
  reference_strain = NULL
)
```

## Arguments

- df1:

  QTL data frame containing association scan results with columns: chr,
  pos, Wald_log10p

- df2:

  Frequency data frame containing experimental evolution data with
  columns: chr, pos, founder, TRT, freq, REP

- dm6_variants:

  Variants data frame containing structural variant information

- dm6_genes:

  Genes data frame containing gene annotations

- chr:

  Character string specifying the chromosome to analyze (e.g., "chr2L")

- start:

  Integer specifying the start position in base pairs

- stop:

  Integer specifying the stop position in base pairs

- reference_strain:

  Optional character string specifying a reference strain to highlight
  in grey

## Value

A combined 5-panel ggplot object with shared X-axis and combined legend
