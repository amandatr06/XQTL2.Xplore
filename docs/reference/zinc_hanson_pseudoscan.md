# Example QTL scan results from ZINC Hanson experiment

This dataset contains QTL scan results for the ZINC Hanson experiment.

## Usage

``` r
zinc_hanson_pseudoscan
```

## Format

A tibble with 25,977 rows and 8 variables:

- chr:

  Chromosome

- pos:

  Genomic position (bp)

- Wald_log10p:

  -log10(p) from Wald test

- Pseu_log10p:

  -log10(p) from Pseudoscan

- Falc_H2:

  Falconer's H2

- Cutl_H2:

  Cutler's H2

- avg.var:

  Average variance

- cM:

  Genetic position (cM)
