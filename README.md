# SPAmix+
A scalable, accurate, and universal analysis framework to control for population structure and family relatedness in large-scale genome-wide association studies (GWAS).

# Comparision of SPAmix+, SPA<sub>GRM</sub> and regular methods

[SPAGRM](https://wenjianbi.github.io/grab.github.io/docs/approach_SPACox.html) extends [SPACox](https://wenjianbi.github.io/grab.github.io/docs/approach_SPACox.html) to analyze a study cohort in which subjects can be genetically related to each other. The method is still only valid to analyze a homogeneous population. **[SPAGRM](https://github.com/HeXuPKU/SPAGRM) can lead to false discoveries or loss of power in analyses of heterogeneous population, although incorporating SNP-derived ancestry PCs as covariates. SPAmix+ can analyze a study cohort in which subjects can be genetically related to each other and from multiple populations.** 

We conduct simulation studies to analyze binary (case-control) traits in a heterogeneous population. We simulate an admixed population of EUR (European) population and EAS (East Asian) population with sample size n = 10000. For each genetic variant, we simulated genotypes using ancestry vectors and allele frequency downloaded from the 1000 Genomes Project. Depending on the difference of MAFs (i.e. DiffMAF = MAF in EUR - MAF in EAS) and the minimal MAF value (i.e. minMAF = min(MAF in EUR, MAF in EAS)) in populations EUR and EAS, genetic variants were categorized into 15 groups. The case-control ratio (prevalence) in EUR was higher or lower than that in EAS.

The empirical type I error rates of SPAmix, SPAGRM, and [REGENIE](https://rgcgithub.github.io/regenie/) were evaluated based on 1000,000 tests at a significance level of 0.00005. If prevalences (or case-control ratios) were the same in EUR and EAS populations, then all methods can control type I error rates well. However, if prevalences (or case-control ratios) were different in EUR and EAS populations, **although incorporating SNP-derived ancestry PCs as covariates, SPAGRM can have inflated or deflated type I error rates** depending on prevalence (case-control ratios) and MAF in EUR and EAS populations. Meanwhile, the other two methods can still control type I error rates reasonably well(see the figure below).

![plot](https://github.com/YuzhuoMa97/SPAmixPlus/blob/main/Simulation%20studies/Figures/typeIerror_rates_pheno_hetero_GRAB_SPAGRM_GRM_I_GRAB_SPAmix_REGENIE.jpeg)

# SPAmix+ can control for population structure and family relatedness

We simulate heterogeneous populations with population-specific MAF and prevalence and evaluate type I error for binary trait analysis based on 100,000 tests. In this situation, SPAmix+ can control for population structure and family relatedness, and SPAGRM had inflated type I error rates (see the figure below).

![plot](https://github.com/YuzhuoMa97/SPAmixPlus/blob/main/Simulation%20studies/Figures/typeIerror_binary_phenotype_SPAmixPlus_test10.jpeg)


