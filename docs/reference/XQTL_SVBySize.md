# Plot structural variants by size

Creates a specialized visualization of structural variants (SVs) showing
their relative sizes within a genomic region. This function displays SVs
as triangles with heights proportional to their size, with deletions
shown below the center line and insertions above. Different SV types are
color-coded and labeled for easy identification.

## Usage

``` r
XQTL_SVBySize(
  variants,
  target_chr,
  target_start,
  target_stop,
  df2,
  reference_strain = NULL
)
```

## Arguments

- variants:

  Data frame containing variant information with REF and ALT columns for
  size calculation

- target_chr:

  Character string specifying the chromosome to analyze (e.g., "chr2L")

- target_start:

  Integer specifying the start position in base pairs

- target_stop:

  Integer specifying the stop position in base pairs

- df2:

  Data frame containing founder frequency data to determine founder
  genotypes

- reference_strain:

  Optional character string specifying a reference strain (not used in
  this plot)

## Value

A ggplot object showing structural variants with sizes represented by
triangle heights
