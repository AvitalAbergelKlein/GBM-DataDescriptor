# GBM-DataDescriptor
TCR Repertoire Analysis in GL261 Glioma Anti-PD-1 Response.

This repository contains scripts for analyzing TCR repertoire data from GL261 glioma mouse model study examining anti-PD-1 immunotherapy responses.

## Dataset Overview
- **Model**: Syngeneic, orthotopic GL261 glioma in mice
- **Treatment Groups**: Anti-PD-1 antibody treatment vs. untreated controls
- **Sample Collection**: Longitudinal sampling up to day 63 post-tumor implantation
- **Sample Types**: 128 samples from PBMCs and tumor tissues
- **Response Rate**: ~30% of treated mice showed therapeutic response

<img width="468" alt="image" src="https://github.com/user-attachments/assets/006c8e36-2d54-478c-865e-e5985335e589" />

## Data Collection and Processing
1. **Blood and Tumor Collection:**
   - Blood samples were collected via tail vein on days 0, 7, 21, 35, 49, and 63 post-tumor cell inoculation.
   - Tumors were collected as endpoint samples progressively throughout the study.
2. **Repertoire Sequencing (Rep-Seq):**
   - TCR sequencing was performed on an Illumina Miseq sequencer using the 600-cycle MiSeq reagent kit v3 (Illumina) with pair-end, 2x300 base pair reads.
   - Sequencing output consisted of FASTQ files for each blood and tumor sample.
3. **Data Validation and qulaity control**
   - fastp was employed to trim raw reads from 300 bp down to 200 bp, addressing quality concerns associated with longer paired-end reads.
   - Quality control for each sample was performed using FastQC, followed by MultiQC to aggregate the results across all samples into a single comprehensive report.
3. **Data Processing with MiXCR:**
   - Raw sequencing reads were processed and clonotypes assembled based on V(D)J recombination patterns using MiXCR software
4. **Concatenation of TRA and TRB Files:**
   - The processed TRA and TRB files were concatenated for further analysis.


## Data Analysis
- **preseq_analysis.Rmd:**
   - This script analyzes pre-sequencing biological data. It includes:
     1. Longitudinal quantification of tumor bioluminescence signals (Fig. 2a).
     2. Group-wise comparison of bioluminescence counts at specific time points (Fig. 2b).
     3. Analysis of mean body weight over time for treated and control groups (Fig. 3).
- **initial_stats_immunearch.Rmd:**
  - This script performs an initial quality control and exploratory analysis of TCR repertoire sequencing data (TRA, TRB, and combined TRA+TRB).
    It calculates basic statistics, including total clone counts, mean clone counts per sample, and mean clonotype counts per sample.
    It also includes a visualization of the distribution of sample counts by time point and class (Fig. 5).
- **tcr_repertoire_diversity_clonality_analysis.Rmd:**
  - After concatenating TRA and TRB files per sample, this script analyzes clonotype and clone counts across classes and time points (Fig. 6), performs clonality assessment after downsampling (Fig. 7), and evaluates diversity metrics (Fig. 8).
    
## Usage
- The analysis can be reproduced by following the steps outlined in each analysis script.

## Data Availability
The raw sequencing data is deposited in the NCBI SRA under accession number [TODOTODO].
