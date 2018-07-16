# LD Score Regression Pipeline

This README provides information to run the LD score regression pipeline for estimation of heritability from single disorders or cross-disorder shared heritability (genetic correlation).
  
## Input data
Input data are GWAS summary statistics, to be provided as .txt files. The following columns are required, required column names are indicated between square brackets:
1. SNP name (usually rs-number) [SNP].
2. Effect allele (not necessarily the minor allele, but this should be the allele that the effect size refers to) [A1].
3. Other allele [A2].
4. Association p-value [P].
5. Effect size [BETA].