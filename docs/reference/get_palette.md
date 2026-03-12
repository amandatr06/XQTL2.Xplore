# Get color palette for founders

Creates a color palette for founder strains, with optional highlighting
of a reference strain in grey. This function is used internally by
plotting functions to ensure consistent color schemes across different
visualizations.

## Usage

``` r
get_palette(founders, reference_strain = NULL)
```

## Arguments

- founders:

  Character vector of founder names

- reference_strain:

  Optional character string specifying a reference strain to highlight
  in grey

## Value

Named character vector with founder names as names and hex color codes
as values
