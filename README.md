# SPAmix+
A scalable, accurate, and universal analysis framework to control for population structure and family relatedness in large-scale genome-wide association studies (GWAS).

# Comparision of SPAmix+, SPA<sub>GRM</sub> and regular methods

[SPAGRM](https://wenjianbi.github.io/grab.github.io/docs/approach_SPACox.html) extends [SPACox](https://wenjianbi.github.io/grab.github.io/docs/approach_SPACox.html) to analyze a study cohort in which subjects can be genetically related to each other. The method is still only valid to analyze a homogeneous population. **SPAGRM can lead to false discoveries in analyses of heterogeneous population, although incorporating SNP-derived ancestry PCs as covariates. SPAmix+ can analyze a study cohort in which subjects can be genetically related to each other and from multiple populations.** 

We conduct simulation studies to analyze binary (case-control) traits in a heterogeneous population. We simulate an admixed population of EUR (European) population and EAS (East Asian) population with sample size n = 10000. For each genetic variant, we simulated genotypes using ancestry vectors and allele frequency downloaded from the 1000 Genomes Project. Depending on the difference of MAFs (i.e. DiffMAF = MAF in EUR - MAF in EAS) and the minimal MAF value (i.e. minMAF = min(MAF in EUR, MAF in EAS)) in populations EUR and EAS, genetic variants were categorized into 15 groups. The case-control ratio (prevalence) in EUR was higher than that in EAS.
