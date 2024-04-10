# ChIP2MACS2

This repository contains a short pipeline to simplify peak calling from ChIP-seq data. The pipeline is currently as follows: 
1. First, raw data (in .fastq or .fq format) is trimmed using TrimGalore!
2. Trimmed data is aligned to a reference genome using Bowtie2
3. picard MarkDuplicates is used to mark duplicate reads in the sequence output. 
4. MACS2 is then used to call peaks. 