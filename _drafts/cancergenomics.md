
Course outline
http://ftp.ebi.ac.uk/pub/training/2020/Cancer_Genomics_20/

# Day 1

## Ajay Mishra - Welcome presentation

No comments

## Mathieu Bourgey - NGS introduction

* Novaseq - read how it distinguishes itself
    * What exactly are flow cells
    * Sequencing by synthesis (Illu)
* PacBio
    * How exactly does this work?
* Oxford Nanopore
    * Reading 5-mers
* Library technology
    * 10x genomics
* Key parameters
    * Library type
    * Read length
    * Error profile
    * Cost/barcoding potential (multiplexing)
    * Turnaround time
* Types of sequencing libraries
    * Mate-pair libraries (?)
    * Single-end read
    * Paired-end read
* Longer reads are useful in assemblies, and in transcriptomics (isoforms)
* Multiplexing / barcoding
* Short read issues
    * Many letters you need to fit
    * Sometimes they don't - sequencing errors, SNP, structural variants
    * Sometimes they fit in many places - low complexity regions, microsatellite, repeat regions
* DNA-seq
    * Whole genome sequencing
        * SNV detection
        * Structural variants
        * Capture regulatory region information
        * Cancer analysis
        * De-novo genome assembly
    * Whole exome sequencing
        * Cheaper
        * Rare disease analysis (why?)
* Structural variants
    * Deletion
    * Novel sequence insertion
    * Mobile element insertion
    * Tandem duplication
    * Interspersed duplication
    * Inversion
    * Translocation
* Handling tumor data
    * Compare tumor to matched normal sample
        * Detect somatic events
        * Remove noise
        * Detect sample mix-up (!)
    * Use scDNA approach
        * Confirm somatic event (?)
        * Get ride of the cellularity (?)
        * Detect clonal events - SNV, CNV (?)
* RNA-seq
    * Small exons that may be separated by large introns
        * Mapping to genome challenging
        * Ribosomal and mitochondria genes misleading
    * Small RNAs must be captured separately
    * RNA is fragile and easily degraded
    * Common secondary analysis
        * Gene expression and DE (raw, or RPKM/FPKM)
        * Transcript discovery and annotation (assembly)
        * Allele specific expression - link SNPs to gene expression
        * Mutation discovery (not advisable?)
        * Fusion detection
        * RNA editing
    * Fusion transcripts can only be detected on RNA level
* Epigenetics
    * Changes in gene expression not encoded by underlying DNA
        * Histone modification (accessibility, compaction)
        * DNA methylation
* ChIP-seq
    * Mapping of protein-DNA interaction on genome scale
    * Can be used to detect binding sites (combination with antibodies to find the proteins)
    * For RNAseq, compare different experiments (why here?)
    * Motif analysis
* Tumor data
    * Many histone modifications are robust cancer biomarkers
* Methylation
    * one of the most commonly occuring metagenomic events in mammalian genome
    * Plays a role in silencing genes and in X-chromosome inactivation
    * Plays a role in establishment and maintenance of "imprinted genes" (?)
    * Bisulfite sequencing is a technology that can be used to detect methylations?
    * Can play a role for rate of cancer progression
* Summary
    * Illumina
        * <1% bases miscalled
        * Up to 600 Gbp per run
    * Pacbio/Oxford nanopore
        * >50kb bp reads
        * 5-10 Gbp per run
        * Higher error rate (5-15%)
        * Can detect modified bases (methylation?)

## Tobias Rausch - Cancer genomics and epigenetics

### Cancer genomics and its caveats

* Sequencing provides snapshot in time and space
* DNA-sequencing can provide
    * Tumor phylogeny & tumor evolution
    * Tumor cell content (tumor purity)
    * Tumor heterogeneity (subclonality)
    * Tumor ploidy (number of copies of each chromosome)
    * Interplay of somatic and germline mutations (elaborate)
* Whole genome duplication - pretty common in many cancer types
* Tumor heterogeneity and tumor evolution
* Complexity in bulk sequencing - many cancer types are sequenced together
* Germline versus somatic variants
    * Germline
        * Present in egg or sperm
        * Inherited
        * May be predisposing (two-hit hypothesis) and may cause cancer family syndrome
    * Somatic variants
        * Not heritable
        * Non-germline tissue
        * Only passed to descendants of that mutant cell
        * Different in each cancer, where recurrence indicates selective advantage
* Germline BRCA1 mutations (PTVs ?) influence somatic mutation landscape
* Cancer genomics data analysis
    * DNA variant detection (snv, indel)
    * Careful here with sequencing errors - insertions, deletions, basecalling errors
* Higher-level variant discovery
    * Short indels
    * Copy-number variations (CNVs)
    * Structural variants (SVs)
* Cancer genomics workflow
    * Tumor BAM + Normal BAM
    * Variant genotyping
    * Variants from germline + somatic + wildtype
    * Distinguish somatic mutations from germline mutations
* Challenges in somatic variant calling
    * Usual assumptions does not hold
        * Diploid genome
        * Homogeneous sample (no subclones)
        * Pure sample
    * Somatic calling sensitivity decreases rapidly for tumor in normal contamination
    * Verification by orthogonal method often required
        * PCR & Sanger
        * Target capture (?)
* Sequencing depth
    * 30x often too low for cancer genomics
* Estimating tumor parameters
    * Read-depth segmentation
    * SNP allele frequencies
    * Somatic variant allele frequency
    * External supporting data
        * Digital karyotype
        * Tumor cell content estimation by pathologists
* Tumor / Normal read depth ratio
    * Read counting in windows for tumor and normal data
    * Log2 ratio for each window
    * Chromosome-wide plot
* Variant allele frequency
    * Copy number variants will cause shift in B-allele frequency of het. SNPs
    * Allele frequency is influenced by tumor purity
* LOH (?) to estimate purity?
* Further caveats
    * Human errors
        * Sample swaps
        * Cross-sample contamination
        * DNA-quality (FFPE, degraded DNA)
    * Visually check allele frequencies normal to tumor
    * Check for contaminated germline (?)
    * Check for read-group/lane swaps
* Mutational signatures
* Large-scale chromosome abberrations (structural variants)
* Additional challenges in somatic structural variant calling
    * Comprehensive detection usually requires complementary assays and additional normalizaion techniques (GC content)
    * Breakpoints are often imprecise
    * Baseline is not necessarily copy-number 2
    * Incomplete copy-number polymorphism map
    * Incomplete understanding of SV mechanisms & structure
    * Methods tend to have high false positive rate
    * Complex rearrangements are difficult to disentangle
    * SV detection usually requires WGS, exome data provides incomplete view
* Summary - keep in mind
    * Samples
        * Avoid low-input or degraded DNA (FFPE samples are risky)
        * Pathologists can overestimate tumor purity
        * Include matched control and be aware of tumor in normal contamination
    * Library construction & sequencing parameters
        * Check duplication rates, multiple libraries reduce PCR error rates
        * Higher coverage is needed for impure tumors & heterogeneous tumors
        * Clonal architecture cannot be inferred with 30x
        * WES is not suitable for CNV & SV detection
    * Variant calling
        * Sub-clonal variants (<15% VAF) are difficult to detect
        * Using multiple callers is valuable in practice
        * Indels and SV are more difficult to detect
        * Samples from multiple time-points / locations help tracking clonal evolution and inferring the clonal architecture of tumor specimen
    * Validations
        * Orthogonal sequencing methods (PCR + sanger, targeted/custom capture, arrays, long-read sequencing) to help assess variant calling FDRs
        * Interpreting somatic variants can be facilitated by means of integrating transcriptome (RNA-seq) and epigenome datasets with genomics read outs

# Day 2

## Mathieu Bourgey - SNV introduction

## Robert Eveleigh - DNA-seq processing introduction

https://github.com/mbourgey/EBI_cancer_workshop_SNV

## Tobias Rausch - Structural variants

# Day 3

## Mathieu Bourgey - Introduction CNV and data interpretation

## Robert Eveleigh - Workshop

https://github.com/mbourgey/EBI_cancer_workshop_SNV
https://github.com/mbourgey/EBI_cancer_workshop_visualization

# Day 4

## Alexey Larionov - RNA-seq lecture

Including data, handouts, scripts

## Francesco Iorio - Cancer genomics hands-on

# Day 5

# Wendi Bacon - Dropseq
