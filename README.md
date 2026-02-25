# XQTL2.Xplore Repository

This repository contains the XQTL2.Xplore R package for XQTL (Experimental Quantitative Trait Locus) analysis and visualization.

## Package Overview

XQTL2.Xplore provides comprehensive tools for:
- **Genome-wide QTL visualization** with Manhattan plots
- **Regional analysis** with peak refinement tools
- **Frequency change analysis** across experimental conditions
- **Gene and variant annotation** visualization
- **Publication-ready multi-panel plots**

## Quick Installation

### Method 1: Install from GitHub (Recommended)
```r
# Install remotes if not already installed
if (!requireNamespace("remotes", quietly = TRUE)) {
  install.packages("remotes")
}

# Install the package
remotes::install_github("tdlong/XQTL2.Xplore")

# Load and test
library(XQTL2.Xplore)
```

### Method 2: Install from local source
```r
# Clone the repository first, then:
# In R, set working directory to the package folder
setwd("path/to/XQTL2.Xplore")

# Install devtools if needed
if (!requireNamespace("devtools", quietly = TRUE)) {
  install.packages("devtools")
}

# Install the package
devtools::install()
```

## Test Installation

After installation, test that everything works:

```r
# Load the package
library(XQTL2.Xplore)

# Check available data
data(package = "XQTL2.Xplore")

# Load and examine example data
data(zinc_hanson_pseudoscan)
data(zinc_hanson_means)
data(dm6.ncbiRefSeq.genes)
data(dm6.variants)

# Quick test - should work without errors
head(zinc_hanson_pseudoscan)
```

## Demo

**Quick Context:** [Example study](https://academic.oup.com/genetics/article/231/3/iyaf173/8239421)

X-QTL mapping of multiparental Drosophila population to identify genomic loci associated with zinc toxicity resistance. This identified 10 genes with significant genotype-by-treatment effects, including pHCl-2, which encodes a zinc sensor protein. This provides a pathway to a broader understanding of the biological impact of metal toxicity.

**Test the core functionality:**

```r
# Load the package and data
library(XQTL2.Xplore)
data(zinc_hanson_pseudoscan)
data(zinc_hanson_means)
data(dm6.ncbiRefSeq.genes)
data(dm6.variants)

# Find a peak in a genomic region
out <- XQTL_zoom(zinc_hanson_pseudoscan, "chr3R", 18000000, 20000000, 3, 3)

# View the zoomed region
print(out$plot)

# Create a publication-ready 5-panel plot
XQTL_5panel_plot(zinc_hanson_pseudoscan, zinc_hanson_means, 
                 dm6.variants, dm6.ncbiRefSeq.genes, 
                 out$chr, out$start, out$stop)
```
**Expected output:**

<img src="img/sample_data1.png"> # need to create image folder!!!

**Description:**
1. **Top panel (Wald_log10p):** This is the QTL signal strength. The black line (peaking around 32 on the –log10 p-value scale) shows an exceptionally strong statistical signal of association with zinc resistance in this region.

2. **Second panel (Frequency(Z-C):** Haplotypes above zero (black line - A7) have higher zinc resistance while those below zero (green line - A3) have a lower zinc resistance.

3. **Third panel (Gene tracks):** Blue rectangles indicate exons from 5' to 3' and orange 3' to 5'. These are candidate genes located under the QTL peak that could be potential contributors to zinc resistance.

4. **Last panel (Founders and Genomic Position):** These display differences in each of the 8 founder lines (A1–AB8). Each row corresponds to one founder, and the triangles/symbols indicate structural variants (SV) type and location:
    - Upward triangles = deletions (DEL), insertions (INS), etc.
    - Red filled symbols = mobile element insertions (DEL:rME, INS:ME)
    - The large red arrow near 18.930–18.940 Mb (labeled E and F) is a particularly large or notable SV in founders A5/A7/AB8

## Documentation & Learning

### Vignettes (Interactive Tutorials)

```r
# setwd("path to where XQTL2.Xplore is located on your device") 

# Load specific vignettes
file.edit("XQTL2.Xplore/vignettes/XQTL2_workflow.Rmd")
file.edit("XQTL2.Xplore/vignettes/XQTL2_usage.Rmd")
```

### What You'll Learn in the Vignettes:

** XQTL2_workflow**: Complete analysis workflow from genome-wide exploration to detailed peak analysis
- Step-by-step QTL analysis process
- Peak refinement techniques
- Publication-ready multi-panel plots
- Real data examples throughout

** XQTL2_usage**: Comprehensive function reference with examples
- All plotting functions demonstrated
- Data format requirements
- Customization options
- Advanced usage patterns

### Key Functions Demonstrated in Vignettes:
- **`XQTL_Manhattan_5panel()`** - Genome-wide QTL visualization
- **`XQTL_zoom()`** - Peak detection and regional analysis
- **`XQTL_5panel_plot()`** - Publication-ready multi-panel plots
- **`XQTL_genes()`** - Gene annotation visualization
- **`XQTL_variantsByFounder()`** - Variant analysis across founders
- **`XQTL_change_average()`** - Frequency change analysis

## Key Features

- **Example datasets** included for immediate use
- **Comprehensive vignettes** with complete workflows
- **Publication-ready plots** with customizable themes
- **Efficient data processing** for large genomic datasets
- **Multiple visualization options** for different analysis stages

## System Requirements

- R version 3.5 or higher
- **Minimal dependencies**: Only essential packages required
- **Optional**: Bioconductor packages only needed for custom data preparation
- RStudio (recommended) or R console

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Support

- Check the [vignettes](vignettes/) for usage examples
- Review the [installation guide](INSTALL.md) for troubleshooting
- Open an issue on GitHub for bug reports or feature requests

## Citation

If you use this package in your research, please cite:

```
XQTL2.Xplore: An R package for XQTL analysis and visualization
Author: Tony Long
Version: 0.0.0.9000
URL: https://github.com/tdlong/XQTL2.Xplore
``` 
