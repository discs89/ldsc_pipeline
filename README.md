# LD Score Regression pipeline

This README provides information for running the LD score regression pipeline on single traits (for estimating heritability) or multiple traits (for estimating heritability and genetic correlation).
[LD Score regression methodology](https://www.nature.com/articles/ng.3406) has been published in Nature Genetics by Bulik-Sullivan *et al.*, and the software [can be found on GitHub](https://github.com/bulik/ldsc/). Also refer to this page for detailed information about installation of the software and required python libraries.

### Input data

The input for this LD score regression pipeline are GWAS summary statistics, to be provided in plain text format.

Mandatory input columns are (required column name between brackets):  
1. SNP identifier, usually rs-numer (SNP).  
2. Effect allele, the allele which the effect size refers to (A1).  
3. Other allele of the SNP (A2).  
4. Association p-value of the SNP (P).  
5. Effect size of the A1 allele (BETA).  

Optional columns include (required column name between brackets):  
6. Sample size for SNP in the GWAS (N).  
7. INFO/imputation quality metric (INFO).
  
Besides GWAS summary-level data it is recommended to download a list of good quality HapMap SNPs, as suggested on the LDSC GitHub. When an INFO columns is provided in the summary-level data, this file will be ignored. Furthermore, a reference panel (e.g. 1000 genomes, PLINK binary format) for the calculation of LD scores is required.  

### Calculation of LD scores

LD scores are essential to estimate heritability and genetic correlation. The calculation of LD scores is specific to a population, because LD structures in the genome differ between population. It is not specific to a certain phenotype or input GWAS. This means that if you want to test GWAS studies on *n* different genotypes that were all performed in populations with similar ancestry, you have to calculate LD scores only once. In practice the calculation of LD scores is a time consuming step in this analysis, and therefore it is provided as a separate step in this pipeline.  

  


### Munge summary statistics

As a preparatory step, GWAS summary statistics need to be 'munged' to filter reliable SNPs that can be used for heritability or genetic correlation estimation and get the data in a correct format for LDSC.
Munging can be performed using the script munge_sumstats.sh
This script requires the following arguments:  
1. Path to GWAS summary-level data file, with columns included as specified above.  
2. A custom name of the GWAS (this will be assigned to output files).  
3. Sample size of the GWAS (will be ignored when a sample size column is provided).  

An example command could thus look like this:
  
```
./munge_sumstats.sh /path/to/my_gwas.txt interesting_phenotype 47000
```
  
If a munged file with the given name already exists, the script terminates.  
  

### Estimate heritability and genetic correlation

After munging the summary statistics, the output can be used in heritability and genetic correlation analysis


