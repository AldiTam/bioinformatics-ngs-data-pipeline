# 📖 Abstract
This project provides a comprehensive analysis of Hepatitis C Virus (HCV) genetic variability using public data from the Sequence Read Archive (SRA). Despite effective antiviral treatments, the lack of a universal vaccine—hindered by HCV's high genetic variability—remains a major global health challenge. This work focuses on the HCV E2 envelope glycoprotein, a primary target for neutralizing antibodies and key to vaccine development.

A robust computational workflow was developed to process and analyze raw SRA data, describe the genetic variability of HCV, and identify stable, immunogenic mutations within the E2 glycoprotein's hypervariable region 1 (HVR1). The findings aim to deepen our understanding of HCV genetic diversity and provide a foundation for future vaccine design efforts. For comparative analysis, the workflow was also applied to Respiratory Syncytial Virus (RSV) data.

# 🧬 Project Workflow
The core of this project is an automated bioinformatics pipeline designed to process raw sequencing data from the SRA and perform downstream analysis

An overview of the bioinformatics pipeline used to process raw SRA data.

# 💻 Technical Details
**Key Analyses Performed**
* Genotype Clustering: HCV contigs were clustered using MMseqs2 to identify genotype distribution.

* Phylogenetic Analysis: An unrooted phylogenetic tree was built with Fasttree to visualize the evolutionary relationships between genotypes.

* Variability Analysis: Genetic diversity was quantified using Shannon Entropy and Single Nucleotide Variant (SNV) frequency.

* Protein Stability Prediction: The impact of amino acid mutations on the stability of the E2 glycoprotein was predicted using DeepDDG.

**Core Software & Tools**

* Environment: Miniconda

* Workflow management: Snakemake

* Data Retrieval: SRA-Toolkit

* Quality Control: fastp

* De novo Genome Assembly: SPAdes

* Sequence Alignment & Search: BLASTn, MAFFT

* Sequence Clustering: MMseqs2

* Phylogenetics: Fasttree

* Analysis: Custom Python scripts

# 🚀 Getting Started
Follow these instructions to set up the environment and run the workflow.

## 1. Environment Setup with Miniconda

```bash
# Create a new conda environment (e.g., named 'sra_workflow_env')
conda create --name sra_workflow_env

# Activate the environment
conda activate sra_workflow_env
```

## 2. Install Dependencies

Install all the required bioinformatics tools into the active Conda environment.

```bash
# SRA-Toolkit for downloading and handling SRA data
conda install -c bioconda sra-tools

# Fastp for quality control and trimming
conda install -c bioconda fastp

# SPAdes for de novo genome assembly
conda install -c bioconda spades

# BLAST for sequence searching
conda install -c bioconda blast

# MAFFT for multiple sequence alignment
conda install -c bioconda mafft

# MMseqs2 for clustering
conda install -c bioconda mmseqs2

# FastTree for phylogenetics
conda install -c bioconda fasttree
```

## 3. Usage
The workflow can be run using the snakefile with the tools installed above.

**Step 1: Obtain SRA Accession List**

* Go to the NCBI SRA database (https://www.ncbi.nlm.nih.gov/sra).

* Search for your organism of interest (e.g., "Hepacivirus hominis").

* Use filters to select the desired data (e.g., RNA, Paired-end, Illumina).

* Click "Send to" -> "File" -> Format "Accession List" to download a ```sra_acc_list.txt``` file.

**Step 2: Run the Workflow**
* The main pipeline can be executed via the snakefile
```bash
snakemake --cores #of cores
```
