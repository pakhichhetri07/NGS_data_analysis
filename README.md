## Dataset

Dataset: https://www.ncbi.nlm.nih.gov/sra/?term=ERR361748
SRA Database ID: ERR361748
Curated dataset contains two files labeled as “subset 1 (133.8 MB)” and “subset 2 (139.5 MB)”, both derived from ERR361748
Citation: Ryan, D., & Wolff, J. (2017). MethylSeq_2017 [Data set]. Zenodo. https://doi.org/10.5281/zenodo.557099

## Download dataset instruction
Visit SRA (Sequence Read Archive) database "https://www.ncbi.nlm.nih.gov/sra/"
Select for the SRR ID "https://www.ncbi.nlm.nih.gov/sra/?term=ERR361748"

Commands: 
prefetch ERR361748
Fasterq-dump ERR361748
fasterq-dump ERR361748 --maxsize 100000

## Quality Control
Download & Install FastQC tool 
Link: https://www.bioinformatics.babraham.ac.uk/projects/download.html#fastqc
Locate the downloaded tool & run command 
fastqc subset_1.fastq
fastqc subset2.fastq


