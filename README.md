# transFDR: Trans-ethnic false discovery rate
# Introduction
**transFDR** denotes the trans-ethnic genetic overlap detection method.

From a statistical perspective, under some modeling assumptions, we observe that the trans-ethnic genetic similarity analysis can be implemented with the similar principle of pleiotropic analysis for genetically correlated phenotypes. In the past decade many pleiotropy methods have been proposed; among them, conditional FDR is a popular pleiotropy-informed approach and can be considered a novel generalization of the popular FDR from the single phenotype case to the same phenotype case in the trans-ethnic setting. Therefore, we referred to our used method as transFDR to distinguish itself from conditional FDR.

Therefore, transFDR is simply expressed as transFDR=max(FDR1|2, FDR2|1). Finally, SNPs with transFDR less than a given significance threshold can be prioritized to be population-common genetic loci.

transFDR is implemented in the R statistical environment.
# Required input data
transFDR requires two types of input data:

SNP-level summary ststistics of two populations in terms of effect size and their standard error are required as inputs.

Summary statistics, e.g.,
```ruby
               P.x         P.y
rs10000011     0.065    0.440
rs1000002      0.800    0.220
rs10000036     0.160    0.710
...

```
The summary statistics file should be at least four columns (i.e. P.x and P.y). P.x is the p-value of SNPs in one population; P.y is the p-value of SNPs in the other population.

# Example
```ruby
source("transFDR.R")
input_pvalues = read.table("sample.txt",sep="\t",header=T)
result= transFDR(input_pvalues$P.x,input_pvalues$P.y)

fit12         fit21         fit
0.8978125  0.1338235  0.8978125
1.0139535  3.5545455  3.5545455
0.9070968  0.2120000  0.9070968
...

```
# Cite
Jiahao Qiao<sup>$</sup>, Yuxuan Wu<sup>$</sup>, Shuo Zhang<sup>$</sup>, Yue Xu, Ping Zeng<sup>#</sup> and Ting Wang<sup>#</sup> (2023). Evaluating replicability of European-associated index SNPs in the East Asian population for 31 complex phenotypes.

# Contact
We are very grateful to any questions, comments, or bugs reports; and please contact [Ping Zeng](https://github.com/biostatpzeng) via zpstat@xzhmu.edu.cn.
