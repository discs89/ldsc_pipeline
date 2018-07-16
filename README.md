# LD Score Regression pipeline

This README provides information for running the LD score regression pipeline on single traits (for estimating heritability) or multiple traits (for estimating heritability and genetic correlation).
[LD Score regression methodology](https://www.nature.com/articles/ng.3406) has been published in Nature Genetics by Bulik-Sullivan *et al.*, and the software and detailed information [can be found on GitHub](https://github.com/bulik/ldsc/)
Detailed information about the LD score regression method can be found here: 

### Input data

The input for LD score regression are GWAS summary statistics, to be provided in plain text format.

Mandatory input columns are (required column name between brackets):  
1. SNP identifier, usually rs-numer (SNP).  
2. Effect allele, the allele which the effect size refers to (A1).  
3. Other allele of the SNP (A2).  
4. Association p-value of the SNP (P).  
5. Effect size of the A1 allele (BETA).  

Optional columns include (required column name between brackets):  
6. Sample size for SNP in the GWAS (N).  


### Munge summary statistics

As a preparatory step, GWAS summary statistics need to be 'munged' to filter reliable SNPs that can be used for h2 or rg estimation and get the data in a correct format for LDSC.
Munging can be performed using the script munge_sumstats.sh
This script requires the following arguments:  
1. Path to GWAS summary-level data file, with columns included as specified above.  
2. A custom name of the GWAS (this will be assigned to output files).  
3. Sample size of the GWAS (will be ignored when a sample size column is provided).  

An example command could thus look like this:

```
./munge_sumstats.sh /path/to/my_gwas.txt interesting_phenotype 47000
```


