# ChIP2MACS2

This repository contains a short shell pipeline to simplify peak calling from ChIP-seq data. The pipeline is currently as follows: 
1. First, raw data (in .fastq or .fq format) is trimmed using TrimGalore!
2. Trimmed data is aligned to a reference genome using Bowtie2
3. picard MarkDuplicates is used to mark duplicate reads in the sequence output. 
4. MACS2 is then used to call peaks. 

## References
- BROAD INSTITUTE 2014. picard. 3.1.1 ed.
- DANECEK, P., BONFIELD, J. K., LIDDLE, J., MARSHALL, J., OHAN, V., POLLARD, M. O., WHITWHAM, A., KEANE, T., MCCARTHY, S. A., DAVIES, R. M. & LI, H. 2021. Twelve years of SAMtools and BCFtools. GigaScience, 10.
- KRUEGER, F. & ANDREWS, S. R. 2011. Bismark: a flexible aligner and methylation caller for Bisulfite-Seq applications. Bioinformatics, 27, 1571-1572.
- LANGMEAD, B. & SALZBERG, S. L. 2012. Fast gapped-read alignment with Bowtie 2. Nature Methods, 9, 357-359.
- MARTIN, M. 2011. Cutadapt removes adapter sequences from high-throughput sequencing reads. 2011, 17, 3.
- ZHANG, Y., LIU, T., MEYER, C. A., EECKHOUTE, J., JOHNSON, D. S., BERNSTEIN, B. E., NUSBAUM, C., MYERS, R. M., BROWN, M., LI, W. & LIU, X. S. 2008. Model-based Analysis of ChIP-Seq (MACS). Genome Biology, 9, R137.
