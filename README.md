# Gene expression units and calculations


**RPM or CPM (Reads per million mapped reads or Counts per million mapped reads)**

Counts per million (CPM) is a normalization method commonly used in genomics and transcriptomics to account for differences in sequencing depth or library size when comparing gene expression levels across samples.

Here's how CPM is calculated:

1. **Total Counts**: First, calculate the total number of sequencing reads (or counts) for each sample. This represents the library size or sequencing depth of each sample.

2. **Normalization**: Divide the count of each gene by the total count for the corresponding sample.

3. **Scaling**: Multiply the result by a million to scale the counts to a common reference point, allowing for comparison between samples.

The formula for calculating CPM for a specific gene $\( g \)$ in a sample $\( i \)$ is:  $\[ CPM_{gi} = \frac{{Counts_{gi}}}{{Total\_Counts_i}} \times 10^6 \]$
                               

Where:
- $\( CPM_{gi} \)$ is the counts per million for gene $\( g \)$ in sample $\( i \)$.
- $\( Counts_{gi} \)$ is the count of gene \( g \) in sample $\( i \)$.
- $\( Total\_Counts_i \)$ is the total count of all genes in sample $\( i \)$.

Counts per million normalization allows for the comparison of gene expression levels between samples, accounting for differences in sequencing depth or library size. This normalization method is particularly useful in RNA-seq experiments, where the number of reads mapped to each gene can vary significantly between samples due to technical factors or biological variability.


**RPKM (Reads per kilobase of transcript per million mapped reads)**

RPKM (Reads Per Kilobase of transcript per Million mapped reads) is a normalization method used in RNA sequencing (RNA-seq) data analysis to measure gene expression levels. It accounts for both the length of the transcripts and the sequencing depth. Here’s an overview of what RPKM is and how it is calculated:

### Understanding RPKM

**RPKM** is designed to compare the expression levels of genes within a single sample by normalizing for:
1. **Transcript length**: Longer transcripts are more likely to have more reads simply because they are longer.
2. **Sequencing depth**: This ensures that differences in the number of reads across samples do not affect the comparison of gene expression levels.

### Calculation of RPKM

The formula to calculate RPKM for a given gene is: $\[ \text{RPKM} = \frac{\text{Number of reads mapping to the gene}}{\left(\frac{\text{Total reads in the sample}}{1,000,000}\right) \times \left(\frac{\text{Length of the gene in base pairs}}{1,000}\right)} \] $

Here's a step-by-step breakdown:

1. **Number of Reads Mapping to the Gene**: Count the number of reads that map to the specific gene.
2. **Total Reads in the Sample**: Calculate the total number of reads obtained from the sequencing experiment.
3. **Length of the Gene**: Determine the length of the gene (transcript) in base pairs.

### Step-by-Step Example

Assume we have:
- **1000 reads** mapping to a gene.
- **20 million total reads** in the sample.
- **2000 base pairs** (bp) length of the gene.

The calculation would be as follows:

1. **Calculate reads per million (RPM)**:
   \[ \text{RPM} = \frac{\text{Total number of reads}}{1,000,000} \]
   \[ \text{RPM} = \frac{20,000,000}{1,000,000} = 20 \]

2. **Normalize for the length of the gene**: b$\[ \text{RPKM} = \frac{\text{Number of reads mapping to the gene}} $
   $ {\text{RPM} \times \left(\frac{\text{Length of the gene}}{1,000}\right)} \]$
   $\[ \text{RPKM} =  \frac{1000}{20 \times 2} = \frac{1000}{40} = 25 \]$

Thus, the RPKM for this gene is 25.

### Key Points

- **Normalization**: RPKM accounts for sequencing depth and gene length, enabling comparison of gene expression levels within a sample.
- **Application**: Useful for identifying highly expressed genes, comparing expression levels within a sample, and detecting differential expression.
- **Limitations**: Not suitable for comparing gene expression across different samples or conditions without further normalization, as it doesn't account for differences in library composition or sequencing biases.


**TPM (Transcripts per million)**


**TPM (Transcripts Per Million)** is a normalization method used in RNA sequencing (RNA-seq) data analysis to measure gene expression levels. It is designed to improve comparability between samples by normalizing for both transcript length and sequencing depth. Here’s an overview of what TPM is and how it is calculated:

### Understanding TPM

TPM is similar to RPKM (Reads Per Kilobase of transcript per Million mapped reads) but with a key difference in the order of normalization steps. TPM normalizes for gene length first and then for sequencing depth, which ensures that the sum of TPMs in each sample is the same, making it easier to compare gene expression levels between different samples.

### Calculation of TPM

The formula to calculate TPM for a given gene is: $ \[ \text{TPM} = \frac{\text{Number of reads mapping to the gene} / \text{Length of the gene in kilobases}}{\sum \left(\text{Number of reads mapping to each gene} / \text{Length of each gene in kilobases}\right)} \times 10^6 \]$

Here's a step-by-step breakdown:

1. **Calculate Reads Per Kilobase (RPK)**: $\[ \text{RPK} = \frac{\text{Number of reads mapping to the gene}}{\text{Length of the gene in kilobases}} \]$

2. **Sum of RPK values for all genes**: $\[ \sum \text{RPK} = \sum \left(\frac{\text{Number of reads mapping to each gene}}{\text{Length of each gene in kilobases}}\right) \]$

3. **Normalize each RPK value to get TPM**: $\[ \text{TPM} = \frac{\text{RPK}}{\sum \text{RPK}} \times 10^6 \]$

### Step-by-Step Example

Assume we have data for three genes with the following properties:

| Gene | Reads | Length (bp) |
|------|-------|-------------|
| A    | 500   | 1000        |
| B    | 1000  | 2000        |
| C    | 1500  | 3000        |

#### Step 1: Calculate RPK for each gene

\[ \text{RPK}_A = \frac{500}{1000 / 1000} = 500 \]
\[ \text{RPK}_B = \frac{1000}{2000 / 1000} = 500 \]
\[ \text{RPK}_C = \frac{1500}{3000 / 1000} = 500 \]

#### Step 2: Sum of RPK values $ \[ \sum \text{RPK} = 500 + 500 + 500 = 1500 \]$ 

#### Step 3: Normalize to get TPM

\[ \text{TPM}_A = \frac{500}{1500} \times 10^6 = 333,333.33 \]
\[ \text{TPM}_B = \frac{500}{1500} \times 10^6 = 333,333.33 \]
\[ \text{TPM}_C = \frac{500}{1500} \times 10^6 = 333,333.33 \]

### Key Points

- **Normalization**: TPM normalizes for gene length first, then for sequencing depth, ensuring that the total TPMs in each sample sum to 1 million.
- **Application**: Useful for comparing gene expression levels between different samples.
- **Advantage**: TPM is more suitable for between-sample comparisons than RPKM/FPKM because it makes the data more comparable by ensuring a consistent total across samples.

### Summary

TPM (Transcripts Per Million) is a robust normalization method in RNA-seq data analysis, designed to account for both transcript length and sequencing depth. It normalizes for gene length first and then for sequencing depth, making it more effective for comparing gene expression levels across different samples. This method is widely adopted in transcriptomics to ensure consistent and comparable expression measurements.

