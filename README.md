# transFDR: Trans-ethnic false discovery rate
# Introduction
**transFDR** is an identification of trans-ethnic genetic overlap detection method. an identification of trans-ethnic genetic overlap detection method.

Over the past few years many methods have been developed for detecting pleiotropy.    Among those, the cFDR method is a pleiotropy-informed method to discover genetic overlap and can be viewed a novel extension of the popular FDR for a single trait in one population to the same trait in trans-ethnic cases. By integrating association results from multiple traits, this method could offer important sights into trans-ethnic genetic overlap and increased statistical power to identify less significant association signals. The null hypothesis of FDR is no association between a genetic variant and the trait of focus in one population. Based on this definition and the principle of FDR, cFDR is logically defined as the posterior probability that a random SNP is null for the trait in one population given that the observed P values for the trait in both populations are less than a predetermined threshold.

As the principal and conditional positions for the trait in cFDR described above are exchangeable between the populations, transFDR is defined in a similar way.   Therefore, transFDR for identifying shared genetic loci is simply expressed as transFDR=max(cFDR1|2, cFDR2|1), which is defined as the probability that a particular SNP has a false positive association with the trait in the two populations given the observed P values. Finally, SNPs with transFDR less than a given significance threshold can be prioritized to be population-common genetic loci.

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
Jiahao Qiao<sup>$</sup>, Yuxuan Wu, Yue Xu, Ping Zeng<sup>#</sup> and Ting Wang<sup>#</sup> (2023). Evaluating replicability of European-associated genetic loci for 31 complex phenotypes in the East Asian population.

# Contact
We are very grateful to any questions, comments, or bugs reports; and please contact [Ping Zeng](https://github.com/biostatpzeng) via zpstat@xzhmu.edu.cn.
