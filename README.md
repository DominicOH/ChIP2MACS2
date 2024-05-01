# ChIP2MACS2

This repository contains a short shell pipeline to simplify peak calling from ChIP-seq data. The pipeline is currently as follows: 
1. Raw data (in .fastq or .fq format) is trimmed using TrimGalore!
2. Trimmed data is aligned to a reference genome using Bowtie2
    - Optional: Reads overlapping blacklisted regions, such as problematic repetitive parts of the genome, can be removed from the resulting sequence files. 
3. picard MarkDuplicates is used to mark duplicate reads in the sequence output 
4. MACS2 is then used to call peaks

## Usage 
Clone the repository to your intended destination and turn it into an executable: 

```
git clone https://github.com/DominicOH/ChIP2MACS2.git
cd ChIP2MACS2
chmod +x ChIP2MACS2
```

Define a conda environment of required packages using the included `environment.yaml` file. 

```
conda env create -f environment.yaml
```

Note: due to conflicting samtools versions (required `samtools >= 1.19.2`) required for this package and MACS2, you may need to explicitly upgrade samtools to correct version.

Add the ChIP2MACS2 script to your path. From there, basic usage is (ensure input files are enclosed by "" if using wildcard characters):

```
ChIP2MACS2 -t <treatment_file(s).fq> -c <control_or_input_files(s).fq> -x <bowtie2_index_prefix>
```

Additional options enable the use of paired-end sequence files (`--paired`) and the inclusion of a BED-format blacklist file to remove unwanted regions (`--blacklist <bed>`). Using `--blacklist` requires the setting of a chromosome sizes file (`--genome <genome.chrom.sizes>`), like those downloadable from UCSC or produced using `samtools faidx`. Note: the included blacklist file must be sorted in the same order as the genome file. 

## References
- ANDREWS, S. 2010. FastQC:  A Quality Control Tool for High Throughput Sequence Data.
- BROAD INSTITUTE 2014. picard. 3.1.1 ed.
- DANECEK, P., BONFIELD, J. K., LIDDLE, J., MARSHALL, J., OHAN, V., POLLARD, M. O., WHITWHAM, A., KEANE, T., MCCARTHY, S. A., DAVIES, R. M. & LI, H. 2021. Twelve years of SAMtools and BCFtools. GigaScience, 10.
- KRUEGER, F. & ANDREWS, S. R. 2011. Bismark: a flexible aligner and methylation caller for Bisulfite-Seq applications. Bioinformatics, 27, 1571-1572.
- LANGMEAD, B. & SALZBERG, S. L. 2012. Fast gapped-read alignment with Bowtie 2. Nature Methods, 9, 357-359.
- MARTIN, M. 2011. Cutadapt removes adapter sequences from high-throughput sequencing reads. 2011, 17, 3.
- ZHANG, Y., LIU, T., MEYER, C. A., EECKHOUTE, J., JOHNSON, D. S., BERNSTEIN, B. E., NUSBAUM, C., MYERS, R. M., BROWN, M., LI, W. & LIU, X. S. 2008. Model-based Analysis of ChIP-Seq (MACS). Genome Biology, 9, R137.
