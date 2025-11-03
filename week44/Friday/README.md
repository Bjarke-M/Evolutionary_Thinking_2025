# Friday Week44

## Population structure of Goats and an introduction to the PCA

We will recreate this research paper to some extent [goat research paper](https://gsejournal.biomedcentral.com/counter/pdf/10.1186/s12711-018-0422-x.pdf) you don't have to read it

Introduction to a PCA by some generative AI (you know of whom I speak)

Principal Component Analysis (PCA) is a versatile statistical technique that finds its utility in a wide array of fields, including genetics, by effectively simplifying complex high-dimensional data while preserving its essential variance. PCA operates by transforming the original data into a new coordinate system, comprised of orthogonal axes known as principal components, which are the linchpin for unraveling significant patterns within the data.

The PCA process commences with standardizing the data to ensure no single variable dominates the analysis. Subsequently, it hinges on the computation of the covariance matrix, which uncovers the interrelationships between variables, reflecting how they co-vary and their linear associations. Eigenvalue decomposition follows, extracting eigenvalues and eigenvectors from the covariance matrix. Eigenvalues unveil the amount of variance that each principal component explains, while eigenvectors define the principal components' directions.

Researchers typically choose a subset of the principal components, ranked by their corresponding eigenvalues, capturing a substantial portion of the variance in the data. This selection can be predicated on predetermined criteria, such as a desired percentage of explained variance. The chosen principal components are then employed to project the original data onto this reduced dimensionality space, resulting in a more compact dataset. The most important point to note is that PCA is **linear** dimensionality reduction technique which makes the interpretation of the results easier as relationships between variables are preserved.

In the realm of population genetics, PCA serves as a powerful tool for diverse applications. It aids in unveiling the genetic structure of populations, effectively visualizing clusters and patterns indicative of different geographic regions or subpopulations. Moreover, PCA plays a pivotal role in quality control, identifying outliers and mixed-ancestry individuals to maintain the integrity of genetic datasets. Additionally, it is instrumental in correcting for population stratification in genome-wide association studies, ensuring more accurate results. Genetic clustering, evolutionary studies, and the elucidation of genetic relatedness among species or subspecies are also well-served by PCA.

In essence, PCA simplifies the complexity of high-dimensional genetic data and empowers researchers to visualize and interpret genetic diversity, evolutionary relationships, and population structures, making it an indispensable tool in the field of population genetics.

You can find the Jupyter notebook for today's session [here](exercise/pca_goats.ipynb).




The answers to the questions in the Jupyter notebook:
1. why drop mitochondrial and sex chromosomes
    
    **Mitochondrial SNPs:** Have different inheritance patterns (maternal only, no recombination). Much higher mutation rates than nuclear DNA. Effectively haploid, which violates assumptions of diploid genetic models.Would create artificial population structure based on maternal lineages rather than genome-wide ancestry
    
    **Sex chromosome SNPs:** Different copy numbers between males (XY) and females (XX). Hemizygous regions in males complicate genotype calling and analysis. Would introduce sex-based clustering that obscures autosomal population structure. Dosage compensation and unique evolutionary pressures make them non-comparable to autosomes
    
2. Why would we want to filter individuals with >5% missing SNPs and SNPs with >5% missing genotypes?
    
    **Missing data issues:** Poor quality samples/SNPs can distort PCA results. Missing data patterns can create artificial clustering. Individuals with high missingness may have technical artifacts (poor DNA quality, sequencing errors). SNPs with high missingness are often poorly called or in problematic genomic regions
    
    The 5% threshold balances retaining sufficient data while excluding low-quality information that could bias population structure inference.
    
3. Why would we want to filter SNPs with MAF < 0.05? What is the MAF and why do we divide by 2 in the calculation?
    
    Rare variants are more susceptible to genotyping errors. Provide less statistical information for inferring population structure. Can be population-specific (private alleles) and create noise rather than capturing shared ancestry patterns. PCA is more effective with common variants that show frequency differences between populations
    
4. Why would we want to impute the missing values before performing the PCA?
    
    **PCA requires complete data matrices:** Standard PCA algorithms cannot handle missing values. Missing data would either require dropping entire samples/SNPs (losing information) or cause computational errors
    
    **Imputation benefits:** Preserves sample size and statistical power. Maintains data structure and relationships. Common methods (mean imputation, LD-based imputation) use population-level information to make reasonable estimates. Prevents bias from non-random patterns of missingness. 
    
    Mean imputation is replace with population allele frequency. assumes HWE
    
5. What does each point in the PCA scatter plot represent? What do the axes represent? 
    
    each point is an individual. Axis show the variation. PC1 explain the highest variation,. 
    
6. What does the percentage of variance explained by each component mean?
    
    So much of the variation in the dataset is explain by this axis. 
    
7. What evolutionary explanations causes populations structure?
    
    genetic drift, migration/gene flow, geographic isolation, founder effect, isolation by distance,  natural selection, admixture.
    
8. How does the population structure of the first two principal components and explained variance change if we apply more stringent missing value filtering or MAF filtering?\
    
    **More stringent missing value filtering (<5%):** Cleaner signal, less noise. May remove individuals from underrepresented populations. Could reduce overall sample size significantly. Generally sharpens population clusters
    
    **More stringent MAF filtering (>0.05):** Focuses on more common, well-characterized variants. May reduce resolution between closely related populations (removes population-specific variants). Can decrease variance explained if rare variants contributed to structure. Typically makes clusters more distinct but may lose fine-scale structure. Reduces total number of SNPs, potentially affecting statistical power
    
9. How does the PCA change if we only consider mitochondrial and sex chromosome SNPs?
    
    **Mitochondrial only:**Would show maternal lineages and phylogeography. Much stronger clustering (no recombination = complete linkage). Different demographic history (smaller effective population size). Higher variance explained per PC. May not match autosomal population structure due to sex-biased processes
    
    **Sex chromosomes only:** Males would show different patterns (hemizygous X). Might need to analyze males and females separately or use specialized methods. X chromosome shows different demographic history (¾ the effective population size of autosomes). Could reveal sex-biased migration patterns. Y chromosome (males only) would show paternal lineages
    
10. What if we visualize the first vs. the third principal component instead of the first two? Compare with the paper.
    
    another clustering → other variation → see paper: explain the variation in Africa mostly. 
    
11. Does the PCA change for different imputation strategies?
    - **Mean imputation** - Replace with population allele frequency (simplest, assumes HWE)
    - **Mode imputation** - Use most common genotype
    - **LD-based imputation** - Use correlations between nearby SNPs (most sophisticated)
    - **Random imputation** - Sample from allele frequency distribution
