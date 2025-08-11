# Polygenic Risk Score (PRS) Workshop Exercise: Cardiovascular Disease 

The exercise walks through the process of calculating and visualizing **Polygenic Risk Scores (PRS)** for Coronary Artery Disease (CAD) using publicly available GWAS data and simulated genotype/phenotype data.

This repository contains an exercise from the MiCM Intro to PRS workshop 
- The exercise material is adapted from code prepared by Dr. Zoe Schmilovich, June 2024
- The exercise data (European portion of 1000 Genomes) is pre-processed by Dr. Kevin Liang, July 2022


## Requirements
We will be using Google Colab to run our analyses.
- https://colab.research.google.com/drive/1wTGopy_T8LjsdJaevI6swChlBzc3ehm5?usp=sharing.<br>

Alternatively, if you would like to run the analyses locally, you will need to have access to the Unix terminal, so be sure you have access to one. 
* Mac OS and any linux distribution will have a terminal already
    * Mac OS: search for terminal in your spotlight search
* Windows users: 
    * Option 1: Download a [unix subsystem (WSL)](https://ubuntu.com/tutorials/install-ubuntu-on-wsl2-on-windows-10#1-overview) **recommended
    * Option 2: Download [MobaXterm](https://mobaxterm.mobatek.net/)


## Learning Objectives

By completing this exercise, you will:

1. Become familiar with `plink2` tool for manipulation of genomic data.
2. Visualize GWAS results with a Manhattan plot and SNP p-value distribution.
3. Perform genotype QC: filtering by MAF, missingness, Hardy–Weinberg equilibrium.
4. LD prune SNPs to ensure independence.
5. Apply precomputed PRS weights to individual-level genotypes.
6. Visualize PRS distribution and test for case–control differences.

> **Note**: This dataset is for educational purposes only. The phenotype labels are simulated and do not represent real disease status.

## Contents
Link to Google Colab: https://colab.research.google.com/drive/1wTGopy_T8LjsdJaevI6swChlBzc3ehm5?usp=sharing

All material for exercise can be found in the `Exercise/` directory
- `scripts` 
  - Step by step instruction for data preprocessing and calculation of PRS
    - This script can be run locally after installing relevant packages (see below) `MiCM_PRS_CAD.ipynb` 
- `data`
  - CAD GWAS summary statistics (van der Harst et al., 2018) https://doi.org/10.1161/CIRCRESAHA.117.312086
    - `raw_cad_gwas_sum_stats` is too large and therefore not on GitHub, please see Google Colab documentation for download instructions 
  - European genotype subset from 1000 Genomes Project
    - `EUR.bim`
    - `EUR.fam`
    - `EUR.bed`
  - Simulated CAD phenotypes assigned to individuals from the 10000 Genomes Project
  - Intermediate files from quality control
    - `CAD_phenotypes.txt `
  - Binary files of participants after SNP filtering for genotyping missingness, allele frequency and Hardy-Weinberg equilibrium
    - `CAD_maf-0.01_geno-0.1_hwe-1e4.bim`
    - `CAD_maf-0.01_geno-0.1_hwe-1e4.bed`
    - `CAD_maf-0.01_geno-0.1_hwe-1e4.fam`
  - Binary files of participants after LD-pruning 
    - `CAD_EUR_QCed.bim`
    - `CAD_EUR_QCed.bed`
    - `CAD_EUR_QCed.fam` 
  - Precomputed PRS weights for CAD
    - `CAD_EUR_pst_eff_a1_b0.5_phiauto_allchr.PLINKscore` 
  - Calculated PRS for individuals
    - `prs_for_cad.sscore`
 
## How to Run

**Option 1 — Google Colab**  
1. open Google colab: https://colab.research.google.com/drive/1wTGopy_T8LjsdJaevI6swChlBzc3ehm5?usp=sharing
2. Run all cells in order.

**Option 2 — Local Execution**  
1. Install dependencies:
   ```bash
   pip install gdown pandas numpy matplotlib seaborn
2. Download ```Exercises/scripts/MiCM_PRS_CAD.ipynb```
2. Install locally command line tools:
  - [`plink2`] Documentation: https://www.cog-genomics.org/plink/2.0/
  - [`gdown`] Documentation: https://pypi.org/project/gdown/

## References
Material adapted from Dr. Zoe Schmilovich and Dr. Kevin Liang
 
*Workshop created as part of the McGill Initiative in Computational Medicine*
