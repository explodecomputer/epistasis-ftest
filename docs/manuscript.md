---
title: Problems with testing for long-range genetic interactions with imperfect information about large additive causal effects
---


## Introduction

An important component of understanding the genetic architecture of complex traits is the extent to which the effect of a particular locus depends on the genotype at another locus, also known as genetic interaction or epistasis. Knowledge of epistatic influences on complex traits may inform biological understanding of their aetiology, contribute towards improved prediction accuracy, and have implications on natural selection. Along with other non-additive genetic components, the contribution of epistatic variance to complex traits is likely to be small, though broad sense heritability estimates which would capture them are seldom reported or decomposed into constituent parts for non-clonal organisms. Instead, researchers have sought to detect interacting genetic loci through association analyses to report instances of epistatic influences on complex traits. 

In a recent review of the literature, it was concluded that of all the many empirical papers that search for epistasis influencing human complex traits it was unlikely that any reported statistical genetic interactions represented robust examples of biological epistasis. The Hemani et al 2014 (H2014) paper, which reported replication of genetic interactions in independent datasets, was listed amongst those examples. In this paper we aim to provide a detailed examination of the statistical test used as it is very widely used but has potential issues which have not yet been described.

### The basic statistical test for 2-locus genetic interactions

Detecting epistatic interactions, should they exist, is difficult for two reasons. First, the statistical power for an interaction term to reach significance, in comparison to a marginal additive effect of similar magnitude, is low. This is because the statistical test typically has a larger number of degrees of freedom, and if the causal variants are not available in the data then loss of signal with decaying LD between the causal variant and the observed variant is squared or quadratic, in comparison to a linear loss for additive effects. Second, the parameter space for two-locus epistasis is O(m^2), hence a much more strict multiple testing correction is required than GWAS under the additive model, if the computational capability exists to test the entire set of pairwise interactions. If not, then the incomplete coverage likely translates into loss of power.

While many methods exist that attempt to circumvent these problems, one analytical strategy has been to conduct the search on traits that are more likely to have larger effects such as gene expression levels. In H2014 a brute force search strategy was performed, applying a 4 d.f. linear model for each pairwise combination of 528,509 autosomal single nucleotide polymorphisms against each of 7,339 gene expression levels. The statistical test attemped to capture any joint effect of two independent variants that was not explained by the marginal additive or dominance effects of either of the variants. 

$$
H_{0}: \sum^{3}_{i=1} \sum^{3}_{j=1} (\bar{x_{ij}} - \bar{x_{i}} - \bar{x_{j}} + \mu)^2 = 0
$$

$$
H_{1}: \sum^{3}_{i=1} \sum^{3}_{j=1} (\bar{x_{ij}} - \bar{x_{i}} - \bar{x_{j}} + \mu)^2 > 0
$$

This effect decomposition is fundamental to basic quantitative genetic theory. The decomposition was originally formulated by Cockerham (1954), and has been used routinely in the linkage study era and the GWAS era (Cordell 2002, Wei et al 2015). The level of epistasis can be tested for statistical significance using an F test with $4,n-9$ degrees of freedom. 

The method was in H2014 with a sample of 846 individuals, and 501 independent pairwise interactions were identified surpassing a permutation-derived threshold of $p < 2.31 \times 10^{-16}$. The majority of these interactions were 'long-range', where the two variants were on different chromosomes. However in almost all cases, one of the variants  In two independent datasets, together comprising 2,131 individuals, 30 of these interactions replicated at a Bonferroni multiple testing correction ($p < 0.05/501$), and 46 replicated at FDR < 0.05. 

### A summary of the problems with the original findings

Soon after publication, these findings were further replicated in an independent dataset by Wood et al (2014). However, with the availability of sequence level genetic data, they were able to fine map the additive effects for each gene expression level where the H2014 genetic interactions were discovered. Upon including the fine-mapped additive effects as covariates in the interaction models they found that most of the interaction effects substantially attenuated. We found a similar attenuation of effects in the original data by using fine mapped imputed additive effects as covariates. At this stage, it became clear the original findings of statistical interactions were difficult to interpret as biological epistasis, along with most reported epistatic signals as they typically arose from this form of test. Importantly, it raised the question of why such a fundamental method was giving rise to unreliable results.

Wood et al (2014) interpreted the original discovery as haplotype effects, a well-known mechanism by which two loci can appear epistatic but be due to a simple additive effect is in the case of haplotype effects. Here, the observed loci flank a causal variant and are each in incomplete linkage disequilibrium with each other and the causal variant. A statistical interaction between the observed loci can capture more of the additive variance of the causal variant than the marginal additive effects of both the observed loci combined. This explanation was unproven but plausable for the set of cis-cis interactions reported, those where the two interacting loci were each close to the gene whose expression levels they were influencing. However it does not explain the cis-trans interactions, where the two interacting loci are on different chromosomes. In this paper we explore the question of how a single unobserved cis-additive effect can give rise to cis-trans statistical associations. We go on to explore how this influences replication rates and potential methods for avoiding the problem.

### Theory

Begin by considering three loci, where locus 1 is an additive causal effect (the cis-additive effect), locus 2 is in high but incomplete linkage disequilibrium with locus 1 (the cis-interacting locus) and locus 3 is uncorrelated with either 1 or 2 (the trans-interacting locus). Using a haploid model for simplicity, for $N$ samples we have a vector $x_{i}$ for each of the three loci ($i \in {1,2,3}$) such that all values of $x_{i} \in {0,1}$. 






### Statistical vs biological epistasis?





### 
