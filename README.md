# RNA-seq Analysis of Viral Nervous Necrosis (VNN) To Study Host-Pathogen Interaction

## Overview
This project investigates host–pathogen interaction in fish cell lines infected with Viral Nervous Necrosis (VNN) using RNA-seq data.  
The goal was to identify differentially expressed genes and understand affected biological pathways across different time points of infection.

## Experimental Design
- Model system: Fish cell lines (in vitro infection)
- Conditions:
  - Day 3 vs Control
  - Day 5 vs Control
  - Day 3 vs Day 5

## Tools Used
- Galaxy platform
- R (DESeq2, clusterProfiler)
- STRING database
- Cytoscape

  ## Analysis Workflow
- Quality Control: FASTQC / Falco
- Trimming: Trimmomatic
- Alignment: HISAT2
- Counting: featureCounts
- Differential Expression: DESeq2
- Functional Enrichment: GO, KEGG (clusterProfiler)
- Network Analysis: STRING + Cytoscape

  # Results

## Day 3 vs Control

### PCA
![PCA](Figures/PCA/PCA_Day3_vs_control.png)

### Heatmap
![Heatmap](Figures/Heatmap/HeatMap_Day3_vs_control.png)

### MA Plot
![MA](Figures/MA/MA_Day3_vs_control.png)

### GO Enrichment
![GO](Figures/GO/GO_Day3_vs_Control.png)

### KEGG Pathway
![KEGG](Figures/KEGG/KEGG_Day3_vs_Control.png)

### PPI Network
![PPI](Figures/PPI/PPI_Day3_vs_Control.png)

**Interpretation:**  
Early infection (Day 3) shows enrichment of protein catabolic and ubiquitin-mediated processes, indicating active protein turnover and initial cellular response to viral infection.

## 🔹 Day 5 vs Control

### PCA
![PCA](Figures/PCA/PCA_Day5_vs_control.png)

### Heatmap
![Heatmap](Figures/Heatmap/HeatMap_Day5_vs_control.png)

### MA Plot
![MA](Figures/MA/MA_Day5_vs_control.png)

### GO Enrichment
![GO](Figures/GO/GO_Day5_vs_Control.png)

### KEGG Pathway
![KEGG](Figures/KEGG/KEGG_Day5_vs_Control.png)

### PPI Network
![PPI](Figures/PPI/PPI_Day5_vs_Control.png)

**Interpretation:**  
Later stage (Day 5) shows enrichment of ribosomal and immune-related processes, suggesting activation of protein synthesis and antiviral defense mechanisms.

## 🔹 Day 3 vs Day 5 (Optional Comparison)

### PCA
![PCA](Figures/PCA/PCA_Day3_vs_Day5.png)

### Heatmap
![Heatmap](Figures/Heatmap/HeatMap_Day3_vs_Day5.png)

### MA Plot
![MA](Figures/MA/MA_Day3_vs_Day5.png)

### GO Enrichment
![GO](Figures/GO/GO_Day3_vs_Day5.png)

### KEGG Pathway
![KEGG](Figures/KEGG/KEGG_Day3_vs_Day5.png)

### PPI Network
![PPI](Figures/PPI/PPI_Day3_vs_Day5.png)

**Interpretation:**  
The comparison between Day 3 and Day 5 highlights a shift from early protein turnover and metabolic processes to enhanced ribosomal activity and immune-related responses, indicating progression toward a coordinated antiviral defense.

