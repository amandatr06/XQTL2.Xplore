# Processed gene annotations for Drosophila melanogaster (dm6)

A dataset containing processed gene annotations from the dm6 NCBI RefSeq
GTF file. The data has been processed to include exon and UTR
information, with positions converted to megabase (Mb) units for easier
plotting.

## Usage

``` r
dm6.ncbiRefSeq.genes
```

## Format

A data frame with the following columns:

- seqnames:

  Chromosome name (e.g., "chr2L")

- start:

  Start position in base pairs

- end:

  End position in base pairs

- start_mb:

  Start position in megabases

- end_mb:

  End position in megabases

- gene_name:

  Gene identifier

- strand:

  DNA strand ("+" or "-")

- is_utr:

  Logical indicating if the region is a UTR

## Source

Processed from dm6.ncbiRefSeq.gtf
