# Advanced-EDA-for-Genomic-Data-Analysis-Identifying-Genetic-Variations-Through-Visualization.

![Project Banner](path_to_your_image.png](https://github.com/Karthik-GigaByte/Image/blob/main/d.jpeg)

## Overview

This project focuses on a comparative genomic analysis between two distinct human populations: Yoruba in Ibadan, Nigeria (YRI), and Utah residents with Northern and Western European ancestry (CEU). By analyzing chromosome 22 (can choose any)from both populations, we aim to identify population-specific genetic variations and understand their potential biological implications.

## Data Sources

The datasets utilized in this project are sourced from the [International Genome Sample Resource (IGSR)](https://www.internationalgenome.org/data-portal). Specifically, we analyzed data from:

- **YRI**: [Yoruba in Ibadan, Nigeria](https://www.internationalgenome.org/data-portal/population/YRI)
- **CEU**: [Utah residents (CEPH) with Northern and Western European ancestry](https://www.internationalgenome.org/data-portal/population/CEU)

## Data Processing Workflow

The analysis involves several key steps:

1. **Data Acquisition**: Download genotype data for chromosome 22 for both YRI and CEU populations.

   ```bash
   # Download VCF file
   sudo curl -O ftp://ftp.1000genomes.ebi.ac.uk/vol1/ftp/data_collections/1000_genomes_project/release/20190312_biallelic_SNV_and_INDEL/ALL.chr22.shapeit2_integrated_snvindels_v2a_27022019.GRCh38.phased.vcf.gz

   # Download corresponding index file
   sudo curl -O ftp://ftp.1000genomes.ebi.ac.uk/vol1/ftp/data_collections/1000_genomes_project/release/20190312_biallelic_SNV_and_INDEL/ALL.chr22.shapeit2_integrated_snvindels_v2a_27022019.GRCh38.phased.vcf.gz.tbi
