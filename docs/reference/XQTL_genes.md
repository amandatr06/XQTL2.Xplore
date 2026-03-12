# Plot genes in a genomic region

Creates a gene track visualization showing gene positions and structures
within a genomic region. This function generates a horizontal gene plot
where each gene is represented as a horizontal line with different
colors for strand orientation (+/-) and different line thicknesses for
coding vs UTR regions.

## Usage

``` r
XQTL_genes(genes, target_chr, target_start, target_stop)
```

## Arguments

- genes:

  Data frame containing gene annotations with columns: chr, start, end,
  gene_name, strand, is_utr

- target_chr:

  Character string specifying the chromosome to analyze (e.g., "chr2L")

- target_start:

  Integer specifying the start position in base pairs

- target_stop:

  Integer specifying the stop position in base pairs

## Value

A ggplot object showing gene annotations in the specified genomic region
