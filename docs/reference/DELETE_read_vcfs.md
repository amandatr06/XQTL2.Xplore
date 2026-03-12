# Read and process multiple VCF files (SLOW - for data creation use create_variants_object.R instead)

Reads and processes multiple VCF files containing different types of
genetic variants (SNPs, INDELs, SVs). This function is designed for data
creation and is computationally intensive. For regular use, the
processed variants data object should be used instead. The function
converts VCF files into a tidy format with standardized genotype coding
and variant classification.

## Usage

``` r
DELETE_read_vcfs(vcf_paths, variant_types, variant_subtypes = NULL)
```

## Arguments

- vcf_paths:

  Character vector of paths to VCF files to process

- variant_types:

  Character vector specifying the type of each VCF file (e.g., "SNP",
  "INDEL", "SV")

- variant_subtypes:

  Character vector specifying the subtype of each VCF file (e.g.,
  "high", "moderate")

## Value

A tidy data frame with columns: CHROM, POS, type, subtype, and recoded
genotype columns for each founder

## Examples

``` r
# Read multiple VCF files
variants <- DELETE_read_vcfs(
  vcf_paths = c("high_impact_snps.vcf", "moderate_impact_snps.vcf"),
  variant_types = c("SNP", "SNP"),
  variant_subtypes = c("high", "moderate")
)
#> Processing high_impact_snps.vcf...
#> Warning: cannot open file 'high_impact_snps.vcf': No such file or directory
#> Error in file(file, "r"): cannot open the connection
```
