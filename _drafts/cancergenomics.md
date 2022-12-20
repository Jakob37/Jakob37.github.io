
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
