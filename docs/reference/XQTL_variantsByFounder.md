# Plot variants by founder

Creates a variant track visualization showing the presence/absence of
genetic variants across founders within a genomic region. This function
displays high-impact SNPs and INDELs as well as structural variants,
with different symbols and colors representing different variant types
and founder genotypes.

## Usage

``` r
XQTL_variantsByFounder(
  variants,
  target_chr,
  target_start,
  target_stop,
  df2,
  reference_strain = NULL,
  verbose = FALSE
)
```

## Arguments

- variants:

  Data frame containing variant information with genotype columns for
  each founder

- target_chr:

  Character string specifying the chromosome to analyze (e.g., "chr2L")

- target_start:

  Integer specifying the start position in base pairs

- target_stop:

  Integer specifying the stop position in base pairs

- df2:

  Data frame containing founder frequency data to determine founder
  order and colors

- reference_strain:

  Optional character string specifying a reference strain to highlight
  in grey

- verbose:

  Logical, whether to print diagnostic information about variants found
  (default: FALSE)

## Value

A ggplot object showing variant positions and genotypes across founders
