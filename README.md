# Genome-Wide Association Study (GWAS) of Height

An end-to-end GWAS pipeline to identify genetic variants associated with height. Integrates genotype and phenotype data, accounts for population structure and relatedness using linear mixed models in R.

---

## Overview

Height is a complex quantitative trait influenced by genetics and environment. This workflow performs GWAS using imputed genotype data to detect variants associated with height while controlling for population stratification and relatedness.

**Goals:**

- Perform GWAS on continuous phenotype (height)  
- Apply rigorous variant-level quality filtering  
- Adjust for population structure with principal components  
- Account for relatedness using a genetic relatedness matrix (GRM)  
- Identify genome-wide significant variants  

---

## Workflow

### 1. Data Exploration
- Load sample annotation and phenotype data  
- Assess:
  - Sample size  
  - Phenotype distribution (height)  
  - Covariates (sex, population)  

- Visualize distribution using histograms and Q-Q plots  

### 2. Variant Filtering
- Evaluate imputed genotype data by:
  - Imputation quality (r²)  
  - Allele frequency (AF)  

- Apply filters:
  - r² > 0.8  
  - 0.01 < AF < 0.99  

- Retain high-quality variants  

### 3. Population Structure (PCA)
- Use precomputed principal components  
- Evaluate variance explained (scree plot)  
- Visualize clustering by population  
- Include top PCs (PC1–PC4) as covariates  

### 4. Relatedness Assessment
- Use GRM to model kinship  
- Identify close and extended relatives  
- Incorporate GRM as random effect in association model  

### 5. Null Model
- Fit linear mixed model with:
  - Outcome: height  
  - Covariates: sex, population, PC1–PC4  
  - Random effect: GRM  

### 6. Association Testing
- Perform single-variant genome-wide association tests (additive model)  
- Generate:
  - P-values  
  - Effect sizes  
  - Minor allele counts  

### 7. Result Evaluation
- Q-Q plot to assess inflation  
- Calculate genomic inflation factor (λGC)  
- Manhattan plot visualization  
- Identify top significant variants and loci  

---

## Technologies

- R  
- GENESIS  
- SNPRelate  
- GWASTools  
- tidyverse  
- qqman  
- ggplot2  

---

## Key Features

- Complete GWAS pipeline from raw data to results  
- Variant quality control and filtering  
- Population stratification adjustment (PCA)  
- Linear mixed model for relatedness correction  
- Comprehensive visualization of results  

---

## Skills Demonstrated

- Genome-wide association analysis  
- Linear mixed modeling  
- Population genetics and PCA  
- Handling and QC of imputed genotype data  
- Statistical analysis of complex traits  
- Data visualization (Q-Q and Manhattan plots)  

---

## Notes

- Height treated as a continuous phenotype  
- Principal components control for ancestry differences  
- GRM accounts for relatedness and reduces confounding  
- Genomic inflation factor (λGC) indicates well-controlled structure  

---

## Author

**Gagan Heda**
