# Improving existing analysis pipeline to identify and analyze cancer driver genes using multi-omics data

## User Manual
#### 1. Introduction
---
This repository contains source code and original/preprocessed datasets for the paper "[Improving existing analysis pipeline to identify and analyze cancer driver genes using multi-omics data](https://www.nature.com/articles/s41598-020-77318-1)". This pipeline aims to systematically integrate state-of-the-art computational tools to identify, characterize the driver genes and then predict their specific subgroups, which establish the basis for the understanding and further validations of driver genes in the future. We divide the work into two parts: (I) IDENTIFICATION and (II) ANALYSIS, in which the specific tasks of each part as follows:

(I) IDENTIFICATION
 - Omics data are as input to identify driver genes by driver gene identification tools

(II) ANALYSIS
 - The four most widely focused analyses are performed to deal with those drivers

The workflow is also be applied to the identification and analysis of driver genes for breast cancer patients. All statistical analyses were performed using R statistical software.

**All data can be downloaded [here](https://github.com/hauldhut/drivergene/tree/master/Data_n_SourceCode). The data and source code should be in the same folder!**

#### 2. Pipeline
---
![Figure1](https://imgur.com/B4831A1.png)
**Figure 1. Improved analysis pipeline for identification and analysis of driver genes.** The scheme comprises two stages: identification and analysis, in which the former uses the OncodriveFML and OncodriveCLUSTL to identify driver genes with somatic mutation data as input, and the latter performs the four most widely focused analyses to deal with those driver genes. Abbreviation: CNV, Copy number variations.

Here, we use the METABRIC breast cancer (BRCA) dataset as an example to demonstrate the general usability of our workflow to (1) identify and (2) analyze the driver genes.
#### 3. Implementation
---
**Step 1:** Identification of driver genes using the two tools [OncodriveCLUSTL](http://bbglab.irbbarcelona.org/oncodriveclustl/analysis) and [OncodriveFML](http://bbglab.irbbarcelona.org/oncodrivefml/analysis#). </br> 
**Step 2:** Enrichment analysis using the tool [g:Profiler](https://biit.cs.ut.ee/gprofiler/gost) </br> 
**Step 3:** Individual gene-clincial feature association analysis
- Pre-processing gene expression data & clinical data: *"1.Clinical-preprocess.R"*
- Association between individual driver genes and survival rates: *"2.Clinical-SA.R"*
- Identify which driver gene is significantly correlated with which clinical feature : *"3.Clinical-corr.R"*

**Step 4:** Co-expressed module-clinical feature association analysis using WGCNA
- Weighted co-expression driver gene network construction: *"1.WGCA-STEPbySTEP.R"*
- Detect associations of functional modules to clinical features, identification of significant genes and hub genes in each of those modules: *"2.Association-significantgenes-and-hubgenes.R"*

**Step 5:** Patient stratification
- Pre-processing clinical data & CNVs data: *"1.CNA-preprocess.R"*
- Patient stratification by the identified driver genes: *"2.CNA-hclut.R"*
- Comparison between the identified patient groups: *"3.CNA-SA.R"* + *"4.CNA-test.R"*

#### 4. Citation
---
Please kindly cite the following paper (and Star this Github repository if you find this tool of interest) if you use the tool in this repo: </br>
```sh
Reference Type: Journal Article
Author: Nguyen, Quang-Huy
Le, Duc-Hau
Year: 2020
Title: Improving existing analysis pipeline to identify and analyze cancer driver genes using multi-omics data
Journal: Scientific Reports
Volume: 10
Issue: 1
Pages: 20521
Date: 2020/11/25
ISSN: 2045-2322
DOI: 10.1038/s41598-020-77318-1
```
Feel free to contact [Quang-Huy Nguyen](https://github.com/huynguyen250896) (huynguyen96.dnu@gmail.com) or [Duc-Hau Le](https://github.com/hauldhut) (hauldhut@gmail.com) for any questions about the paper, datasets, code and results.


