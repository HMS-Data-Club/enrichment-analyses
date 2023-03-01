# Enrichment Analyses
March 1, 2023 

## Setup

Today we're going to be primarily using R. If you don't have R/RStudio installed, you can refer to our guide [here](https://github.com/HMS-Data-Club/Resources/blob/main/Guides/install-r-rstudio.md).

We will be using the [EnrichmentBrowser](http://bioconductor.org/packages/EnrichmentBrowser) package for our analyses in R.

## Introduction to enrichment analyses and enrichment analysis in R

We'll start by looking at [this workbook](https://github.com/HMS-Data-Club/enrichment-analyses/blob/main/scripts/enrichment_analysis.qmd) which goes through a number of enrichment analyses in R using the `EnrichmentBrowser` package on bulk RNA-seq data. We include significant background material on enrichment analyses, but feel free to leave that for later reading. 

The dataset we will be lookng at is found in the [airway](https://bioconductor.org/packages/release/data/experiment/html/airway.html) data package. This package provides a RangedSummarizedExperiment object of read counts in genes for an RNA-Seq experiment on four human airway smooth muscle cell lines treated with dexamethasone. You can find the original paper for this dataset[here](https://pubmed.ncbi.nlm.nih.gov/24926665/). While the workbook walks through the main steps of an analysis, we also included a [short workbook](https://github.com/HMS-Data-Club/enrichment-analyses/blob/main/scripts/summarized_experiment.qmd) on using SummarizedExperiment objects for those who want to dive a bit deeper into the data. 

If you want to look at how to plot top enriched gene sets in R, [this lesson](https://hbctraining.github.io/Training-modules/Tidyverse_ggplot2/lessons/03_ggplot2.html) by the HBC walks through the plotting steps.

**To continue trying out other tools, save your ranked gene list as:**

```r
write.csv(rowData(airSE)[,4], "../data/airwayDEgenes.csv")
```

## Enrichment Analyses in Python

Python is less popular for enrichment analyses than R or standalone software. However, recently a research group released the [GSEApy](https://academic.oup.com/bioinformatics/article/39/1/btac757/6847088) [package](https://gseapy.readthedocs.io/en/latest/index.html). 

We can install `GSEApy` into our conda environmet (or make a new one). 

```
conda install -c bioconda gseapy
```

We can then try running GSEA in Python. Create a new script with the following imports:

```
import pandas as pd
import gseapy as gp
import matplotlib.pyplot as plt
```

## Standalone Tools

**DAVID**

DAVID is a popular tool for enrichment analyses which runs in your web browser. You can try it out [here](https://david.ncifcrf.gov/tools.jsp).

**GSEA**

The GSEA sofware is a downloadable tool which is perhaps the most popular enrichment software for standard enrichment workflows. You can download and try it [here](https://www.gsea-msigdb.org/gsea/index.jsp).

**Revigo**

Revigo is a great tool for post-processing your enrichment results. It helps identify redudant GO terms and reduces your GO results to be more concise and readable. Try inputing your results from another tool [here](http://revigo.irb.hr/).

## Comparison

Choose at least 2 of the above tools (R, Python, DAVID, or GSEA) and try them out on the airway dataset.

- Do you have access to the same collections of gene sets in each tool?
- Are the results the same between the two?
- How easy would it be to run an enrichment analysis on many datasets?
- Do the results make biological sense? 
- Which do you prefer?
