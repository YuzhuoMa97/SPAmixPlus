# SPAmix+
A scalable, accurate, and universal analysis framework to control for population structure and family relatedness in large-scale genome-wide association studies (GWAS).

Please do not hesitate to contact me (yuzhuoma@stu.pku.edu.cn) if you are interested in SPAmix+ or other retrospective saddlepoint approximation methods desigend for GWAS.

# Introduction of Retrospective saddlepoint approximation (Retrospective SPA) approach in GWAS

Retrospective saddlepoint approximation (Retrospective SPA) is a method applied in GWAS. For a score statistic (S=G^TR), retrospective SPA strategy considers genotypes as random variables and approximate the distribution of score statistics conditional on phenotype and covariates.

Retrospective saddlepoint approximation (Retrospective SPA) methods were first proposed in the master's thesis ([马雨茁.经验鞍点近似方法及其在全基因组关联分析中的应用研究.2022.山东大学,MA thesis.doi:10.27272/d.cnki.gshdu.2022.002946.](https://kns.cnki.net/kcms2/article/abstract?v=jkwd3qsBIEKwkKkgMuimTLSEojAEBaWSJzCAd3uOCepX09aaYi1Vhn87HddxnsydAW9MGQHzgdF9Nw93IZ_DZCdJbGAX3C13DfGxpW58VBV273z1eVlg75Je1akPxIDc5iiSpz46iutS1tt9m3MJRg==&uniplatform=NZKPT&language=CHS) 
**DOI：	10.27272/d.cnki.gshdu.2022.002946**.)

Based on the idea in the above master's thesis, we have applied retrospective saddlepoint approximation to several methods including SPAmix (since 2020), SPAmix+ (based on SPAmix since 2024), SPAGxECCT (based on SPAmix since 2021), and SPAGxEmix+ (based on SPAmix since 2024). 

**If you used retrospective saddlepoint approximation method in your proposed methods or tools, please respect the original ideas in the two original works (SPAGxECCT and SPAmix) that first proposed retrospective saddlepoint approximation method and cite the two papers (SPAGxECCT and SPAmix) or the master's thesis ([马雨茁.经验鞍点近似方法及其在全基因组关联分析中的应用研究.2022.山东大学,MA thesis.doi:10.27272/d.cnki.gshdu.2022.002946.](https://kns.cnki.net/kcms2/article/abstract?v=jkwd3qsBIEKwkKkgMuimTLSEojAEBaWSJzCAd3uOCepX09aaYi1Vhn87HddxnsydAW9MGQHzgdF9Nw93IZ_DZCdJbGAX3C13DfGxpW58VBV273z1eVlg75Je1akPxIDc5iiSpz46iutS1tt9m3MJRg==&uniplatform=NZKPT&language=CHS) according to academic standards.** (MLA format citation: [1]马雨茁.经验鞍点近似方法及其在全基因组关联分析中的应用研究.2022.山东大学,MA thesis.doi:10.27272/d.cnki.gshdu.2022.002946.)

For the reasons why these two papers (**SPAGxECCT** (A scalable and accurate framework for large-scale genome-wide gene-environment interaction analysis and its application to time-to-event and ordinal categorical traits) and **SPAmix** (A scalable, accurate, and universal analysis framework using individual-level allele frequency for large-scale genetic association studies in an admixed population)) have not been published yet (**more than three years since retrospective saddlepoint approximation method was proposed in 2021 and published in 2022 [马雨茁.经验鞍点近似方法及其在全基因组关联分析中的应用研究.2022.山东大学,MA thesis.doi:10.27272/d.cnki.gshdu.2022.002946.](https://kns.cnki.net/kcms2/article/abstract?v=jkwd3qsBIEKwkKkgMuimTLSEojAEBaWSJzCAd3uOCepX09aaYi1Vhn87HddxnsydAW9MGQHzgdF9Nw93IZ_DZCdJbGAX3C13DfGxpW58VBV273z1eVlg75Je1akPxIDc5iiSpz46iutS1tt9m3MJRg==&uniplatform=NZKPT&language=CHS)**), please consult the relevant authors and supervisors.

Suggestions or comments on retrospective saddlepoint approximation methods are also welcome.


# SPAmix+ is an extension of SPAmix

In the SPAmix paper (**A scalable, accurate, and universal analysis framework using individual-level allele frequency for large-scale genetic association studies in an admixed population**), we proposed SPAmix framework that is applicable to admixed populations and can incorporate local ancestry information into analyses. However, SPAmix is only designed for unrelated individuals and cannot account for sample relatedness.

**We are preparing the SPAmix+ paper (A scalable and accurate analysis framework accounting for sample relatedness and population structure for large-scale genetic association studies in an admixed population).** In this paper, we extend SPAmix to SPAmix+, a universal analysis framework that accounts for both population structure and sample relatedness. SPAmix+ allows for the incorporation of admixed individuals into analyses. In addition, SPAmix can be extended to SPAmix+(local), which has the ability to incorporates local ancestry.

**Note that the SPAmix paper and the SPAmix+ paper are two different papers, since the algorithm of SPAmix was complete in 2021.** SPAmix has been implemented in R package GRAB.

# Comparision of SPAmix+, SPA<sub>GRM</sub> and regular methods

[SPAGRM](https://wenjianbi.github.io/grab.github.io/docs/approach_SPACox.html) extends [SPACox](https://wenjianbi.github.io/grab.github.io/docs/approach_SPACox.html) to analyze a study cohort in which subjects can be genetically related to each other. The method is still only valid to analyze a homogeneous population. **[SPAGRM](https://github.com/HeXuPKU/SPAGRM) can lead to false discoveries or loss of power in analyses of heterogeneous population, although incorporating SNP-derived ancestry PCs as covariates. SPAmix+ can analyze a study cohort in which subjects can be genetically related to each other and from multiple populations.** 

We conduct simulation studies to analyze binary (case-control) traits in a heterogeneous population. We simulate an admixed population of EUR (European) population and EAS (East Asian) population with sample size n = 10000. For each genetic variant, we simulated genotypes using ancestry vectors and allele frequency downloaded from the 1000 Genomes Project. Depending on the difference of MAFs (i.e. DiffMAF = MAF in EUR - MAF in EAS) and the minimal MAF value (i.e. minMAF = min(MAF in EUR, MAF in EAS)) in populations EUR and EAS, genetic variants were categorized into 15 groups. The case-control ratio (prevalence) in EUR was higher or lower than that in EAS.

The empirical type I error rates of SPAmix, SPAGRM, and [REGENIE](https://rgcgithub.github.io/regenie/) were evaluated based on 1000,000 tests at a significance level of 0.00005. If prevalences (or case-control ratios) were the same in EUR and EAS populations, then all methods can control type I error rates well. However, if prevalences (or case-control ratios) were different in EUR and EAS populations, **although incorporating SNP-derived ancestry PCs as covariates, SPAGRM can have inflated or deflated type I error rates** depending on prevalence (case-control ratios) and MAF in EUR and EAS populations. Meanwhile, the other two methods can still control type I error rates reasonably well(see the figure below).

![plot](https://github.com/YuzhuoMa97/SPAmixPlus/blob/main/Simulation%20studies/Figures/typeIerror_rates_pheno_hetero_GRAB_SPAGRM_GRM_I_GRAB_SPAmix_REGENIE.jpeg)

# SPAmix+ can control for population structure and family relatedness

We simulate heterogeneous populations with population-specific MAF and prevalence and evaluate type I error for binary trait analysis based on 100,000 tests. In this situation, **SPAmix+ can control for population structure and family relatedness, and SPAGRM had inflated type I error rates** (see the figure below).

![plot](https://github.com/YuzhuoMa97/SPAmixPlus/blob/main/Simulation%20studies/Figures/typeIerror_binary_phenotype_SPAmixPlus_test10.jpeg)

# SPAmix+ can test multiple populations with different levels of relatedness.

We simulate heterogeneous populations (sample size n = 10000) with different levels of relateness, MAF, and prevalence. The MAF in population1 was 0.01, and the MAF in population1 was 0.3. The first 5000 subjects (including 500 families with 10 family members) were from population 1, and the remaining 5000 (including 500 families with 10 family members) subjects were from population 2. We simulated genotypes through gene-dropping simulation. We analyzed binary traits. The prevalence (case-control ratio) in population 1 was 0.01 (1:99), and the prevalence (case-control ratio) in population 2 was 0.01 (1:1). We simulated binary traits using logistic mixed model. Two covariates were simulated folowing standard normal distribution and Bernoulli(0.5) distribution, respectively. The random effect (b_i) in population 1 and 2 were simulated following a multivariate normal distribution N(0, tau_pop1 * GRM_pop1) and N(0, tau_pop2 * GRM_pop2), respectively. Let tau_pop1 = 0.1 and tau_pop2 = 5. 

We evaluated type I error rates of SPAGRM and our proposed method SPAmix+. In total, 1000000 tests were conducted. 

**The results demonstrated that SPAGRM cannot control type I error rates, while SPAmix+ can control for population structure with different levels of relatedness.**
![plot](https://github.com/YuzhuoMa97/SPAmixPlus/blob/main/Simulation%20studies/Figures/typeIerror_binary_phenotype_SPAmixPlus_GRAB_SPAGRM_test10_1e6.jpeg)

# SPAmix+ can can control for population structure and family relatedness even in admixed populations with ancestry-specific MAFs and case-control ratios.

We conduct simulation studies to analyze binary (case-control) traits in a heterogeneous population. We simulate an admixed population of EUR (European) population and EAS (East Asian) population with sample size n = 20000, containing 5,000 4-member families. For each genetic variant, we simulated genotypes using ancestry vectors and allele frequency downloaded from the 1000 Genomes Project. Depending on the difference of MAFs (i.e. DiffMAF = MAF in EUR - MAF in EAS) and the minimal MAF value (i.e. minMAF = min(MAF in EUR, MAF in EAS)) in populations EUR and EAS, genetic variants were categorized into 15 groups. The case-control ratio (prevalence) in EUR was higher or lower than that in EAS.

The QQPlots showed that, if prevalences (or case-control ratios) were different in EUR and EAS populations, **although incorporating SNP-derived ancestry PCs as covariates, SPAGRM can have inflated or deflated type I error rates** depending on prevalence (case-control ratios) and MAF in EUR and EAS populations. Meanwhile, SPAmix+ can still control type I error rates reasonably well(see the figure below).
![plot](https://github.com/YuzhuoMa97/SPAmixPlus/blob/main/Simulation%20studies/Figures/binary-type-one-error-1e6-5methods-sigLevel-QQplot_prevalence.id-7.png)

**The results demonstrated that SPAGRM cannot control type I error rates, while SPAmix+ can control for population structure and sample relatedness even in admixed populations.**
