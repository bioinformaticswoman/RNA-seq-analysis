# RNA-seq Differential Expression Analysis of SARS-CoV-2 Infected Cornea Using DESeq2

## Project Overview

This project performs RNA-seq differential expression analysis using public GEO data and the DESeq2 package in R. The analysis compares SARS-CoV-2 infected human cornea samples with mock-treated cornea samples to identify genes that are significantly upregulated or downregulated after infection.

The project uses GEO accession **GSE164073** and focuses on a beginner-friendly but realistic RNA-seq workflow, including data download, metadata preparation, differential expression testing, visualization, and reproducibility using Snakemake.

## Objective

The main objective of this project is to answer the biological question:

> Which genes are significantly differentially expressed in SARS-CoV-2 infected cornea samples compared with mock-treated cornea samples?

This analysis helps identify gene expression changes associated with viral infection and may highlight immune response, antiviral defense, and inflammation-related genes.

## Dataset

- **Source:** Gene Expression Omnibus (GEO)
- **Accession:** GSE164073
- **Data type:** RNA-seq raw count data
- **Samples analyzed:** Human cornea samples
- **Comparison:** SARS-CoV-2 infected vs mock-treated cornea samples

The dataset was accessed using the `GEOquery` package, which retrieves GEO RNA-seq count data and associated sample metadata.

## Tools And Technologies Used

- R
- Google Colab
- DESeq2
- GEOquery
- SummarizedExperiment
- EnhancedVolcano
- pheatmap
- ggplot2
- dplyr
- readr
- Snakemake

## Workflow Summary

The project follows these major steps:

1. Install and load required R and Bioconductor packages.
2. Download public RNA-seq data from GEO.
3. Inspect sample metadata.
4. Select cornea samples only.
5. Define experimental groups: mock and SARS-CoV-2 infected.
6. Create a DESeq2 dataset object.
7. Filter low-count genes.
8. Run DESeq2 differential expression analysis.
9. Extract and annotate results.
10. Identify significant upregulated and downregulated genes.
11. Generate visualizations.
12. Save result tables and plots.
13. Run the full workflow reproducibly using Snakemake.

## Differential Expression Criteria

Genes were considered significantly differentially expressed if they met both criteria:

**adjusted p-value < 0.05**
**absolute log2 fold change >= 1**

## Key Output Files

### Results

| File | Description |
|---|---|
| [DESeq2_all_results.csv](results/DESeq2_all_results.csv) | Complete DESeq2 results for all tested genes |
| [DESeq2_significant_genes.csv](results/DESeq2_significant_genes.csv) | Genes passing the significance threshold |
| [DESeq2_upregulated_genes.csv](results/DESeq2_upregulated_genes.csv) | Significant genes upregulated in infected samples |
| [DESeq2_downregulated_genes.csv](results/DESeq2_downregulated_genes.csv) | Significant genes downregulated in infected samples |
| [summary_table.csv](results/summary_table.csv) | Summary of tested and significant genes |


## Plots

<img width="2100" height="1500" alt="PCA_plot" src="https://github.com/user-attachments/assets/59c3808f-139b-489b-8ee0-5f3b80a0169e" />
PCA plot showing sample clustering

<img width="900" height="700" alt="MA_plot" src="https://github.com/user-attachments/assets/f8e07b98-18d8-4e08-9daa-a5f9d1815e80" />
MA plot showing expression changes across gene abundance

<img width="2400" height="2100" alt="volcano_plot" src="https://github.com/user-attachments/assets/ec03858d-6906-455b-bf03-8a8c3eb354e5" />
Volcano plot showing significance and fold change

<img width="2400" height="2700" alt="top_30_gene_heatmap" src="https://github.com/user-attachments/assets/3d57c405-0633-4205-beb6-7b767019ce7d" />
Heatmap of the top 30 differentially expressed genes

## Visualizations
The project generates the following visualizations:

PCA Plot: Used to check whether samples cluster according to condition.
MA Plot: Shows log2 fold change against average gene expression.
Volcano Plot: Highlights genes with strong fold changes and statistical significance.
Heatmap: Displays expression patterns of the top differentially expressed genes.
Reproducible Workflow With Snakemake
A Snakemake workflow is included so the full pipeline can be reproduced with one command.

To run the workflow:

snakemake --cores 1
If files already exist and you want to rerun everything:

snakemake --cores 1 --forceall
The Snakefile runs the R script located in:

scripts/deseq2_geo_analysis.R
and produces all result tables and plots automatically.

# How To Run This Project In Google Colab
1. Open a new Google Colab notebook.
2. Install and enable R support using rpy2.
3. Install the required R and Bioconductor packages.
4. Run the DESeq2 analysis cells step by step.
5. Generate plots and result tables.
6. Run the Snakemake workflow for reproducibility.
7. Download the result files and plots from Colab.
8. Biological Interpretation

This project identifies genes whose expression changes in cornea tissue after SARS-CoV-2 infection. Upregulated genes may be associated with antiviral defense, interferon signaling, immune activation, or inflammation. Downregulated genes may reflect biological processes reduced or disrupted during infection.

The results provide an exploratory transcriptomic view of how cornea samples respond to SARS-CoV-2 infection.

## Skills Demonstrated
This project demonstrates skills in:

- RNA-seq data analysis
- Differential expression analysis
- R programming
- Bioconductor workflows
- Public database usage with GEO
- Data cleaning and metadata preparation
- Statistical interpretation of gene expression data
- Data visualization
- Reproducible workflow development
- Snakemake pipeline creation
- Scientific communication

## Project Significance
RNA-seq differential expression analysis is a core method in genomics and bioinformatics. This project demonstrates how public sequencing data can be used to investigate biological responses to disease or infection.

By using DESeq2 and a reproducible workflow, this project shows how raw count data can be converted into interpretable biological results and publication-style visualizations.

## Limitations
This is an exploratory analysis using public data. The results should not be interpreted as clinical conclusions. Differentially expressed genes identified in this project may require further validation through additional experiments, functional analysis, or independent datasets.

## Conclusion
This project presents a complete and reproducible RNA-seq differential expression workflow using GEO public data, DESeq2, and Snakemake. The analysis identifies genes associated with SARS-CoV-2 infection in human cornea samples and demonstrates practical bioinformatics skills in data processing, statistical analysis, visualization, and reproducible research.

## Author
Shagun Srivastava
