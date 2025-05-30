### 2. Author (s)- YEAR.md 
# Title:Comparative Transcriptome Analysis of _Agrobacterium tumefaciens_ Reveals the Molecular Basis for the Recalcitrant Genetic Transformation of _Camellia sinesis_ L
Original Authors:  Ke Jin 1,2,†, Na Tian 1,2,†, Jorge Freire da Silva Ferreira 3, Devinder Sandhu 3, Lizheng Xiao 1, Meiyi Gu 1, Yiping Luo 2, Xiangqin Zhang 2, Guizhi Liu 2, Zhonghua Liu 1,2,*, Jianan Huang 1,2,*, Shuoqian Liu 1,2,*

Original Year: 2022 May, 11. 

Replication Authors: Lakpa Sherpa, Faizo Kasule, Kofi Antwi Appiagyei, Lucky Kofi Gbeda, and Rishaniya Parthasarathy 

Replication date: 09May2025

## Original Study 
The study examines why the tea plant (_Camellia sinesis_ L.) is resistant to _Agrobacterium_-mediated transformation (AMT), a critical tool for genetic modification. By comparing AMT in tea leaves to the highly transformable tobacco (_Nicotiana benthamiana_), the authors identify physical and molecular barriers in tea that disrupt _Agrobacterium_ infection, that make it recalcitrant to AMT.
## Methods: 
1.	Bacterial culture: _Agrobacterium tumefaciens_ strain GV3101 was cultured in LB medium at 28 degree Celsius overnight (200 rpm). 
2.	Tea and tobacco leaf disc (0.5cm x 0.5cm) were soaked in bacterial suspension for 20 mins 
3.	Leaved discs were fixed at intervals (D0-D4) for SEM imaging via Hitachi SU8100 SEM to examine how the tea metabolites affect _Agrobacterium tumefaciens_ morphology. 
4.	Transcriptomics: Bacterial RNA was extracted from tea/tobacco co-cultures at D0, D3, D4. rRNA depleted libraries sequenced on Illumina Novaseq. 
Alignment to A. tumefaciens genome+ plasmid (Bowtie2). DEGs inedited (DESeq2, P-adv<0.05) and annotated (GO/KEGG). 
5.	qRT-PCR validation: RNA extracted reversed transcribed to cDNA amplified using TB Green Premix. It was normalized to housekeeping genes (gyrB, dnaC, atu8171). Correlation performed between RNA-seq and qRT-PCTR data (Pearson). 

## Replication Details 
Two pipelines were used to perform data analysis; Galaxy (https://usegalaxy.org/) and confirmed using R. The paper provided only the BioProject number on NCBI. No count matrix or GitHub repository were available. 
Data from the paper that was replicated include:
•	Differential gene expression
•	Gene Ontology enrichment analysis
•	Expression Pattern Analysis of Genes related to Environmental Information Processing
•	Expression Pattern Analysis of genes related to Cellular Processes
•	We added extra analysis to inlcude Principal Component Analysis (PCA) and time course analysis to compare AMT across D0, D3, D4 to track at what time important genes are downregulatedto make tea recalcitrant.

### Data 
-	Source: Sample data and reference genome (_A. tumefaciens_ str. C58) were downloaded from NCBI and EnsemblENA using the BioProject number PRJNA764576.
-	Data quality control: Did  FastQC & MultiQC on the data
-	Trimmed low-quality reads and adapters with Trimmomatic
	
### Data analysis Methods 
Workflow of RNA-Seq were created using HPC, R software and Galaxy (https://usegalaxy.org/) .  
• After quality control checks and trimming
• Reads were aligned to reference genome using HISAT2
• SAM files were converted to BAM files using Samtools
• These were sorted by genomic coordinates followed by indexing
• We continued to sort by name
• HTSeq0count was used to quantify gene expression or count matrix
• R was used to calculate FPKM
• Normalization & PCA was done using R
• DSeq2 was used to analyse differentially expressed genes in R
• DEGs were filtered and visualized in R

### Methodological Differences from Original Study
The major variation was the choice of analysis tools. The original study did not share full code or workflows, while we used Galaxy and R to reproduce and validate results. Additionally, we performed PCA and time-course analysis, which were not included in the original publication.
    
### Results Summary
- Successfully reproduced heatmaps and barplots showing DEG patterns from D3 and D4.
- Observed consistent downregulation of genes in chemotaxis, quorum sensing, and flagellar assembly as reported.
- Major discrepancy: No DEGs detected at D0 using FPKM thresholds, whereas original paper reported 762 DEGs. We hypothesize this may be due to differences in normalization strategy or batch effects not documented in the original methods.
  
## Conclusion 
-	Similar DEG pattern were observed on day 3 and day 4, but not on day 0. 
-	Key genes, especially those involved in chemotaxis, quorum sensing, and flagellar assembly, were consistently downregulated in _Agrobacterium_ exposed to tea.
-	The original paper could be strengthened by analyzing regulatory changes between time points to better understand dynamic gene expression over the infection timeline
-	Time course analysis
-	Paper didn’t provide read me file and code for reproducibility
-	Proper documentation lacking

