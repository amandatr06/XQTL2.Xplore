# Processed variant data for Drosophila melanogaster (dm6)

A dataset containing processed variant information from multiple VCF
files, including SNPs, INDELs, and structural variants. The data has
been processed to include type and subtype information for easy
filtering and visualization.

## Usage

``` r
dm6.variants
```

## Format

A data frame with the following columns:

- CHROM:

  Chromosome name (e.g., "chr2L")

- POS:

  Position in base pairs

- type:

  Variant type ("SNP", "INDEL", or "SV")

- subtype:

  Variant subtype:

  - For SNPs and INDELs: "high" or "moderate" impact

  - For SVs: The structural variant classification from the FL tag

- Additional columns:

  Genotype information for each sample

## Source

Processed from high_impact_snps.vcf, moderate_impact_snps.vcf,
high_impact_indels.vcf, moderate_impact_indels.vcf, and SV.0328.vcf
