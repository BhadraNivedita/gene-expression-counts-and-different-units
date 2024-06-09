# Gene expression units and calculations


Sure, here are brief definitions of CPM, RPKM, TPM, and DESeq2 normalization:

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
