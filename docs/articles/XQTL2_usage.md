# Using XQTL2.Xplore

## Introduction

XQTL2.Xplore provides tools for visualizing XQTL (X-chromosome
Quantitative Trait Locus) data. This vignette demonstrates how to use
the package’s main functions.

## Data Objects

The package includes several pre-processed data objects:

### Reference Data

1.  `dm6.ncbiRefSeq.genes`: Processed gene annotations from the dm6
    reference genome
2.  `dm6.variants`: Processed variant data from multiple VCF files

### Example Datasets

3.  `zinc_hanson_pseudoscan`: QTL scan results from ZINC Hanson
    experiment
4.  `zinc_hanson_means`: Founder frequency data from ZINC Hanson
    experiment

### Updating Data Objects

The data objects can be updated independently using the functions in the
`data-raw` directory:

``` r
# To update the genes data (from GTF file)
source("XQTL2.Xplore/data-raw/create_genes_object.R")
devtools::document()
devtools::install()
data(dm6.ncbiRefSeq.genes)

# To update the variants data (from VCF files)
source("data-raw/create_variants_object.R")
devtools::document()
devtools::install()
data(dm6.variants)

# To update example datasets
source("data-raw/create_example_data.R")
devtools::document()
devtools::install()
data(zinc_hanson_pseudoscan)
data(zinc_hanson_means)
```

Note: The VCF processing is computationally intensive, so only run
`create_variants_object.R` when necessary.

## Basic Usage

### Loading Package Data

``` r
library(XQTL2.Xplore)

# Load reference data
data(dm6.ncbiRefSeq.genes)
data(dm6.variants)

# Load example datasets
data(zinc_hanson_pseudoscan)
data(zinc_hanson_means)
```

### Loading Your Own Data

If you have your own data, you can load it using standard R functions:

``` r
# Load your own QTL scan results
my_qtl_data <- read.table("my_pseudoscan.txt", header = TRUE)

# Load your own frequency data
my_freq_data <- read.table("my_meansBySample.txt", header = TRUE)
```

### Creating Plots

#### Manhattan Plot

``` r
# Using example data
XQTL_Manhattan_5panel(zinc_hanson_pseudoscan)

# Using your own data
XQTL_Manhattan_5panel(my_qtl_data)

# Single Manhattan plot
XQTL_Manhattan(zinc_hanson_pseudoscan)
```

#### Region Plot

``` r
# Using example data
A1 = XQTL_region(zinc_hanson_pseudoscan, "chr3R", 13000000, 15000000, "Wald_log10p")
A2 = XQTL_change_average(zinc_hanson_means, "chr3R", 13000000, 15000000)
A3 = XQTL_genes(dm6.ncbiRefSeq.genes, "chr3R", 13000000, 15000000)

# Using your own data
A1 = XQTL_region(my_qtl_data, "chr3R", 13000000, 15000000, "Wald_log10p")
A2 = XQTL_change_average(my_freq_data, "chr3R", 13000000, 15000000)
A3 = XQTL_genes(dm6.ncbiRefSeq.genes, "chr3R", 13000000, 15000000)
```

#### Finding Peaks

``` r
# Using example data
out = XQTL_zoom(zinc_hanson_pseudoscan, "chr3R", 13000000, 15000000, left_drop = 3, right_drop = 3)

# Using your own data
out = XQTL_zoom(my_qtl_data, "chr3R", 13000000, 15000000, left_drop = 3, right_drop = 3)
```

### Comprehensive Plotting Functions Showcase

XQTL2.Xplore provides a wide range of visualization tools. Here’s a
comprehensive overview:

#### 1. Genome-wide Analysis

``` r
# 5-panel Manhattan plot (recommended for high-resolution analysis)
XQTL_Manhattan_5panel(zinc_hanson_pseudoscan, cM = FALSE)

# Traditional Manhattan plot with custom color schemes
XQTL_Manhattan(zinc_hanson_pseudoscan, cM = FALSE, color_scheme = "UCI")
XQTL_Manhattan(zinc_hanson_pseudoscan, cM = TRUE, color_scheme = "Stanford")
```

#### 2. Regional Analysis

``` r
# QTL association in a specific region
XQTL_region(zinc_hanson_pseudoscan, "chr3R", 18000000, 20000000, "Wald_log10p")

# Frequency changes between treatment and control
XQTL_change_average(zinc_hanson_means, "chr3R", 18000000, 20000000)
XQTL_change_average(zinc_hanson_means, "chr3R", 18000000, 20000000, plotSelection = TRUE)

# Frequency changes by replicate
XQTL_change_byRep(zinc_hanson_means, "chr3R", 18000000, 20000000)
```

#### 3. Gene and Variant Visualization

``` r
# Gene annotations in a region
XQTL_genes(dm6.ncbiRefSeq.genes, "chr3R", 18000000, 20000000)

# Variant analysis across founders
XQTL_variantsByFounder(dm6.variants, "chr3R", 18000000, 20000000, zinc_hanson_means)

# Structural variants by size
XQTL_SVBySize(dm6.variants, "chr3R", 18000000, 20000000, zinc_hanson_means)
```

#### 4. Publication-ready Multi-panel Plots

``` r
# Complete 5-panel visualization
XQTL_5panel_plot(zinc_hanson_pseudoscan, zinc_hanson_means, 
                 dm6.variants, dm6.ncbiRefSeq.genes, 
                 "chr3R", 18000000, 20000000)

# Custom multi-panel layouts using patchwork
library(patchwork)
A1 <- XQTL_region(zinc_hanson_pseudoscan, "chr3R", 18000000, 20000000, "Wald_log10p")
A2 <- XQTL_change_average(zinc_hanson_means, "chr3R", 18000000, 20000000)
A3 <- XQTL_genes(dm6.ncbiRefSeq.genes, "chr3R", 18000000, 20000000)
A4 <- XQTL_variantsByFounder(dm6.variants, "chr3R", 18000000, 20000000, zinc_hanson_means)

# Custom layout
(A1 / A2) | (A3 / A4)
```

#### 5. Peak Refinement and Analysis

``` r
# Find and refine peak boundaries
out <- XQTL_zoom(zinc_hanson_pseudoscan, "chr3R", 18000000, 20000000, 3, 3)

# View the refined peak
print(out$plot)

# Use refined boundaries for detailed analysis
XQTL_5panel_plot(zinc_hanson_pseudoscan, zinc_hanson_means, 
                 dm6.variants, dm6.ncbiRefSeq.genes, 
                 out$chr, out$start, out$stop)
```

### Customizing Plots

All plotting functions use ggplot2 and can be customized using standard
ggplot2 syntax:

``` r
# Example: Customizing a Manhattan plot
p = XQTL_Manhattan(zinc_hanson_pseudoscan)
p + theme_minimal() + 
    labs(title = "My Custom Title")
```

### Working with Large Regions

For large genomic regions, consider using the zoom function to identify
interesting peaks:

``` r
# First find a peak
out = XQTL_zoom(zinc_hanson_pseudoscan, "chr3R", 13000000, 15000000)

# Then plot the region around the peak
A1 = XQTL_region(zinc_hanson_pseudoscan, out$chr, out$start, out$stop, "Wald_log10p")
A2 = XQTL_change_average(zinc_hanson_means, out$chr, out$start, out$stop)
A3 = XQTL_genes(dm6.ncbiRefSeq.genes, out$chr, out$start, out$stop)
```

### Data Format Requirements

Your data should follow these formats:

- **QTL scan data**: Columns `chr`, `pos`, `Wald_log10p`, and optionally
  `cM`
- **Frequency data**: Columns `chr`, `pos`, `TRT`, `REP`, `founder`,
  `freq`
- **Gene data**: Columns `chr`, `start`, `end`, `gene_name`, `strand`,
  `is_utr`
- **Variant data**: Columns `CHROM`, `POS`, `type`, `subtype`, and
  genotype columns for each founder

## References

- NCBI RefSeq: <https://www.ncbi.nlm.nih.gov/refseq/>
- VCF Format Specification:
  <https://samtools.github.io/hts-specs/VCFv4.2.pdf>
