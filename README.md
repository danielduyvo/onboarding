# Onboarding instructions for dry lab work

These are a set of markdown files, scripts and more for getting started with doing bioinformatics and computational work. These assume that the reader is not familiar with coding and will go through the steps for installing and running different tools and analyses.

```{bash}
echo hello world
```

## Tools and analyses (TODO)

* Programming essentials
    * Visual Studio Code
        * Terminal
    * Git
    * R Studio
        * Tidyverse
    * Jupyter Notebook
* Analyses
    * Downloading data
        * dbGaP
        * Synapse
    * Quality control and pre-processing
        * Genotypes
            * plink
            * bcftools
            * Imputation
                * TOPMed and Michigan imputation server
        * RNAseq
            * Alignment with STAR
            * Pseudoalignment salmon
            * Quality metrics
                * FASTQC
                * Picard Tools
                * samtools
                * RSeQC
                * RNASeQC v2
    * GWAS
        * fastGWA with GCTA
        * SAIGE
    * Heritability analysis
        * GREML with GCTA
        * MultiResponseVarianceComponentModels.jl
    * TWAS
        * isoTWAS
        * SMR
    * WGCNA
    * scRNAseq
* Plotting
    * ggplot2
    * Makie.jl
* Programming extras
    * Vim and NeoVim
