# Determine SV subtype from INFO field

Classifies structural variants into specific subtypes based on the INFO
field from VCF files. This function parses the INFO field to identify
different types of structural variants including deletions (DEL),
insertions (INS), inversions (INV), and their specific subtypes like
complex rearrangements (COM), mobile element insertions (ME), and copy
number variations (CNV).

## Usage

``` r
determine_sv_subtype(info)
```

## Arguments

- info:

  Character string containing the INFO field from a VCF file

## Value

Character string specifying the SV subtype classification
