# XQTL2.Xplore Repository

This repository contains the XQTL2.Xplore R package for XQTL (Experimental Quantitative Trait Locus) analysis and visualization.

## 📦 Package Overview

XQTL2.Xplore provides comprehensive tools for:
- **Genome-wide QTL visualization** with Manhattan plots
- **Regional analysis** with peak refinement tools
- **Frequency change analysis** across experimental conditions
- **Gene and variant annotation** visualization
- **Publication-ready multi-panel plots**

## 🚀 Quick Installation

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

## ✅ Test Installation

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

## 📚 Documentation

- **[Package README](README.md)** - Complete package documentation
- **[Installation Guide](INSTALL.md)** - Detailed installation instructions
- **[Vignettes](vignettes/)** - Tutorials and examples

## 🎯 Key Features

- **Example datasets** included for immediate use
- **Comprehensive vignettes** with complete workflows
- **Publication-ready plots** with customizable themes
- **Efficient data processing** for large genomic datasets
- **Multiple visualization options** for different analysis stages

## 📖 Usage Examples

```r
# Load example data
data(zinc_hanson_pseudoscan)
data(zinc_hanson_means)

# Genome-wide analysis
XQTL_Manhattan_5panel(zinc_hanson_pseudoscan, cM = FALSE)

# Peak refinement
out <- XQTL_zoom(zinc_hanson_pseudoscan, "chr3R", 18000000, 20000000, 3, 3)

# Publication-ready plot
XQTL_5panel_plot(zinc_hanson_pseudoscan, zinc_hanson_means, 
                 dm6.variants, dm6.ncbiRefSeq.genes, 
                 out$chr, out$start, out$stop)
```

## 🔧 System Requirements

- R version 3.5 or higher
- **Minimal dependencies**: Only essential packages required
- **Optional**: Bioconductor packages only needed for custom data preparation
- RStudio (recommended) or R console

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 📞 Support

- Check the [vignettes](vignettes/) for usage examples
- Review the [installation guide](INSTALL.md) for troubleshooting
- Open an issue on GitHub for bug reports or feature requests

## 📊 Citation

If you use this package in your research, please cite:

```
XQTL2.Xplore: An R package for XQTL analysis and visualization
Author: Tony Long
Version: 0.0.0.9000
URL: https://github.com/tdlong/XQTL2.Xplore
``` 