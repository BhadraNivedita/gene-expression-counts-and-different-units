# Gene expression units and calculations

Brief definitions of CPM, RPKM, TPM, and DESeq2 normalization:

### CPM (Counts Per Million)
**Definition**: CPM is a normalization method that accounts for sequencing depth by scaling raw read counts to the number of reads per million total reads in the sample.
**Mathematical Definition**: 
$\[ \text{CPM} = \frac{\text{Number of reads mapping to a gene}}{\text{Total number of reads in the sample}} \times 10^6 \]$

### RPKM (Reads Per Kilobase of transcript per Million mapped reads)
**Definition**: RPKM normalizes read counts by both the length of the gene and the total number of reads in the sample, allowing comparison of gene expression within a sample.
**Mathematical Definition**: 
$\[ \text{RPKM} = \frac{\text{Number of reads mapping to a gene}}{(\text{Length of the gene in kilobases} \times \text{Total number of reads in the sample})} \times 10^9 \]$

### TPM (Transcripts Per Million)
**Definition**: TPM is similar to RPKM but normalizes gene length first, ensuring the sum of TPMs is the same across samples, which is useful for comparing gene expression between samples.
**Mathematical Definition**: 
$\[ \text{TPM} = \frac{\frac{\text{Number of reads mapping to a gene}}{\text{Length of the gene in kilobases}}}{\sum \left(\frac{\text{Number of reads mapping to each gene}}{\text{Length of each gene in kilobases}}\right)} \times 10^6 \]$

### DESeq2 Normalization
**Definition**: DESeq2 normalization is a method used in differential gene expression analysis that accounts for variations in sequencing depth and RNA composition. It uses a median of ratios approach to normalize counts.
**Mathematical Definition**: 
$\[ \text{Normalized count} = \frac{\text{Raw count}}{\text{Size factor}} \]$
(Size factors are calculated to account for differences in sequencing depth and RNA composition across samples.)

These methods ensure that comparisons of gene expression are meaningful by adjusting for various biases and differences in sequencing data.


 ** Why do we need different definitions? 
In bioinformatics, especially in RNA sequencing (RNA-seq) data analysis, we need different normalization units like CPM, RPKM, TPM, and DESeq2 normalization to account for various biases and ensure accurate and meaningful comparisons of gene expression levels. Here’s why these different normalization methods are necessary:

### 1. Sequencing Depth Variation

Different samples can have different total numbers of reads due to variations in sequencing depth. Normalization accounts for these differences, allowing for meaningful comparisons across samples.

- **CPM (Counts Per Million)**: Normalizes for sequencing depth by scaling raw read counts to the number of reads per million total reads in the sample.

### 2. Gene Length Variation

Longer genes are more likely to have more reads mapped simply because of their length. Normalizing for gene length ensures that comparisons of expression levels are not biased by gene size.

- **RPKM (Reads Per Kilobase of transcript per Million mapped reads)**: Normalizes for both gene length and sequencing depth, allowing for comparison of gene expression within a sample.
- **TPM (Transcripts Per Million)**: Similar to RPKM, but first normalizes for gene length and then for sequencing depth. This ensures that the total expression values are comparable across samples, making TPM more suitable for between-sample comparisons.

### 3. RNA Composition Bias

Different samples may have different compositions of RNA species, affecting the total number of reads and their distribution. Effective normalization needs to adjust for these compositional differences to ensure accurate comparisons.

- **DESeq2 Normalization**: Uses a median of ratios approach to normalize counts, accounting for variations in sequencing depth and RNA composition across samples. This method is particularly useful for differential gene expression analysis.

### Why Different Methods?

Each normalization method has specific strengths and is suitable for different purposes:

- **CPM**: Simple and quick, useful for initial data exploration and visualizations.
- **RPKM**: Useful for comparing gene expression levels within a single sample by accounting for gene length and sequencing depth.
- **TPM**: Better suited for comparing gene expression levels between samples because it normalizes the total expression level across samples, ensuring comparability.
- **DESeq2 Normalization**: Provides robust normalization for differential expression analysis, especially when comparing multiple conditions or samples.

### Summary

Normalization is crucial in RNA-seq data analysis to correct for technical biases, allowing for accurate and meaningful biological interpretations. The choice of normalization method depends on the specific goals of the analysis, whether it's comparing expression within a sample, between samples, or identifying differentially expressed genes across conditions.
