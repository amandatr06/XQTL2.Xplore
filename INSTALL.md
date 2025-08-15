# Installation Guide for XQTL2.Xplore

## Quick Installation

For most users, the package can be installed directly from GitHub:

```r
# Install from GitHub
if (!requireNamespace("remotes", quietly = TRUE)) {
  install.packages("remotes")
}
remotes::install_github("tdlong/XQTL2.Xplore")
```

## Alternative Installation Methods

### Method 1: Using remotes (Recommended)
```r
if (!requireNamespace("remotes", quietly = TRUE)) {
  install.packages("remotes")
}
remotes::install_github("tdlong/XQTL2.Xplore")
```

### Method 2: Using devtools
```r
if (!requireNamespace("devtools", quietly = TRUE)) {
  install.packages("devtools")
}
devtools::install_github("tdlong/XQTL2.Xplore")
```

### Method 3: Local installation
```r
# Clone the repository first, then:
setwd("path/to/XQTL2.Xplore")
if (!requireNamespace("devtools", quietly = TRUE)) {
  install.packages("devtools")
}
devtools::install()
```

## Test Your Installation

After installation, verify everything works:

```r
# Load the package
library(XQTL2.Xplore)

# Check what's available
ls("package:XQTL2.Xplore")

# Check available data
data(package = "XQTL2.Xplore")

# Load example data
data(zinc_hanson_pseudoscan)
data(zinc_hanson_means)

# Quick test - should work without errors
head(zinc_hanson_pseudoscan)
dim(zinc_hanson_pseudoscan)
```

## Dependencies

### Required Dependencies (automatically installed)
- **ggplot2** - For data visualization
- **dplyr** - For data manipulation
- **tidyr** - For data reshaping
- **vcfR** - For VCF file processing
- **patchwork** - For combining plots
- **rlang** - For tidy evaluation
- **tibble** - For modern data frames
- **grid** - For plot layout utilities

### Optional Dependencies (only if you need to create data objects)
If you need to process your own GTF files or create new data objects, you'll also need:

```r
# Install Bioconductor packages for data preparation
if (!requireNamespace("BiocManager", quietly = TRUE)) {
  install.packages("BiocManager")
}
BiocManager::install(c("rtracklayer", "GenomicRanges"))
```

**Note**: These Bioconductor packages are NOT required for normal package usage.

## Troubleshooting

### Common Issues

1. **Package not found**: Make sure you're using the correct repository URL
2. **VCF file reading errors**: Make sure `vcfR` is properly installed
3. **Plot combination issues**: Ensure `patchwork` is installed
4. **Data manipulation errors**: Verify `dplyr` and `tidyr` are up to date

### Installation Errors

If you get dependency errors:

```r
# Update all packages first
update.packages(ask = FALSE)

# Then try installation again
remotes::install_github("tdlong/XQTL2.Xplore")
```

### Minimal Installation Test

```r
# Test basic functionality
library(XQTL2.Xplore)
data(dm6.ncbiRefSeq.genes)
data(dm6.variants)

# Should work without errors
head(dm6.ncbiRefSeq.genes)
head(dm6.variants)
```

## Development Installation

For developers who want to modify the package:

```r
# Clone the repository
git clone https://github.com/tdlong/XQTL2.Xplore.git
cd XQTL2.Xplore

# Install in development mode
devtools::install()
```

## System Requirements

- R version 3.5 or higher
- Sufficient memory for large genomic datasets
- Graphics device that supports ggplot2 