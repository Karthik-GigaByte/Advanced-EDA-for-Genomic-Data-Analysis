# Advanced-EDA-for-Genomic-Data-Analysis-Identifying-Genetic-Variations-Through-Visualization.

![Project Banner](https://github.com/Karthik-GigaByte/Image/blob/main/d.jpeg)

## Overview

This project focuses on a comparative genomic analysis between two distinct human populations: Yoruba in Ibadan, Nigeria (YRI), and Utah residents with Northern and Western European ancestry (CEU). By analyzing chromosome 22 (can choose any)from both populations, we aim to identify population-specific genetic variations and understand their potential biological implications.

## Getting Started

To replicate or build upon this analysis:

### Clone the Repository:

   ```bash
     git clone https://github.com/Karthik-GigaByte/Advanced-EDA-for-Genomic-Data-Analysis-Identifying-Genetic-Variations-Through-Visualization.git
     cd Advanced-EDA-for-Genomic-Data-Analysis-Identifying-Genetic-Variations-Through-Visualization.

   ```
### Install Dependencies:

Ensure that `bcftools` and `tabix` are installed on your system. Installation instructions is provide below.



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
   ```
2. **Sample Filtering**: Extract and retain only the samples corresponding to YRI and CEU populations.

   ```bash
   # List all samples in the VCF
   sudo bcftools query -l ALL.chr22.shapeit2_integrated_snvindels_v2a_27022019.GRCh38.phased.vcf.gz > vcf_samples.txt
   
   # Filter for CEU samples
   grep -Fx -f CEU_samples.txt vcf_samples.txt > filtered_CEU_samples.txt
   
   # Create a VCF with only CEU samples
   sudo bcftools view -S filtered_CEU_samples.txt -Oz -o CEU_chr22.vcf.gz ALL.chr22.shapeit2_integrated_snvindels_v2a_27022019.GRCh38.phased.vcf.gz
   
   # Index the new VCF file
   tabix CEU_chr22.vcf.gz
   ```
   Repeat the above steps for YRI samples.

3. **Statistical Analysis**: Perform statistical analyses to identify and compare genetic variations.
   ```bash
   # Generate statistics for CEU
   bcftools stats CEU_chr22.vcf.gz > CEU_stats.txt
   
   # Count the number of samples in YRI
   bcftools query -l CEU_chr22.vcf.gz | wc -l
   ```

## Analytical Steps

The project encompasses the following analyses:

1. **Allele Frequency Calculation**: Determine allele frequencies from genotype data.

2. **Population-Specific Variation Comparison**: Identify and compare genetic variations unique to each population.

3. **SNP Annotation**: Utilize Variant Effect Predictor (VEP) for annotating identified SNPs.

4. **Visualization**: Generate Manhattan plots, Fst distribution histograms, and scatter plots of Fst vs. -log10(P-Value).

5. **Significant SNP Identification**: Highlight SNPs with significant differences between populations.

6. **Allele Frequency Comparison**: Contrast allele frequencies between YRI and CEU to pinpoint notable disparities.

## Data Availability

All datasets and results generated during this project are available in this repository under the `data/` and `results/` directories, respectively.

## Contributing

Contributions are welcome! Please fork the repository and submit a pull request with your proposed changes.

