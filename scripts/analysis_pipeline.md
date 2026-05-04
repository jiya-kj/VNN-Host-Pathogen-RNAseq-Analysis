# RNA-seq Analysis Pipeline

This document outlines the computational workflow used to analyze RNA-seq data from VNN-infected fish cell lines.

## 1. Quality Control
- Tool: Falco (Galaxy)
- Purpose: Assess the quality of raw sequencing reads and identify potential issues such as low-quality bases or sequencing bias.

## 2. Read Trimming
- Tool: Trimmomatic (Galaxy)
- Purpose: Remove adapter sequences and low-quality regions to improve read quality for downstream analysis.

## 3. Read Alignment
- Tool: HISAT2 (Galaxy)
- Purpose: Align high-quality reads to the reference genome.
- Output: SAM/BAM files for further analysis.

## 4. Gene Expression Quantification
- Tool: featureCounts (Galaxy)
- Purpose: Count reads mapped to each gene to generate a gene expression matrix.

## 5. Differential Gene Expression Analysis
- Tool: DESeq2 (R)
- Filtering Criteria: padj_thresh <- 0.05
                      logfc_thresh <- 1
- Significant genes:
  sig <- res %>% filter(padj < padj_thresh)
- Upregulated genes:
  up <- sig %>% filter(log2FoldChange > logfc_thresh)
- Downregulated genes:
  down <- sig %>% filter(log2FoldChange < -logfc_thresh)

## 6. Functional Annotation
- Tool: Biomart (Ensembl, dataset: drerio_gene_ensembl)
- Purpose: Map gene identifiers to Ensembl IDs, Entrez IDs, and gene names.

mart <- useMart("ensembl", dataset = "drerio_gene_ensembl")
mapping <- getBM(
  attributes = c("external_gene_name", "ensembl_gene_id", "entrezgene_id"),
  filters = "external_gene_name",
  values = genes,
  mart = mart
)

## 7. Gene Ontology (GO) Enrichment Analysis
- Tool: clusterProfiler (R)
- Database: org.Dr.eg.db
- Ontology: Biological Process (BP)
- Purpose: Identify overrepresented biological processes among differentially expressed genes to understand functional changes during infection.

  ego <- enrichGO(
  gene = sig_entrez,
  OrgDb = org.Dr.eg.db,
  keyType = "ENTREZID",
  ont = "BP",
  pvalueCutoff = 0.05
)

## 8. KEGG Pathway Enrichment Analysis
- Tool: clusterProfiler (R)
- Organism: Zebrafish (dre)
- Purpose: Identify significantly enriched biological pathways to understand the molecular mechanisms and signaling pathways affected by infection.

  ekegg <- enrichKEGG(
  gene = sig_entrez,
  organism = "dre",
  pvalueCutoff = 0.05
)

## 9. Protein–Protein Interaction (PPI) Network Analysis
- Tool: STRING database and Cytoscape
- Purpose: Explore interactions between proteins encoded by differentially expressed genes and identify key hub genes involved in host response.
- Method:
  1. Upload gene list to STRING database
  2. Import interaction network into Cytoscape
  3. Use CytoHubba plugin for network analysis
  4. Identify hub genes using the Maximal Clique Centrality (MCC) algorithm

## Summary
This pipeline integrates preprocessing, alignment, quantification, differential expression, functional enrichment, and network analysis to investigate host–pathogen interaction in VNN-infected fish cell lines.


