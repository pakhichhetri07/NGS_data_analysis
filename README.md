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
Tool used: FastQC
Download & Install FastQC tool 
Link: https://www.bioinformatics.babraham.ac.uk/projects/download.html#fastqc
Locate the downloaded tool & run command 
fastqc subset_1.fastq
fastqc subset2.fastq

## Trimming
Install Cutadapt 
Link: https://cutadapt.readthedocs.io/en/stable/installation.html
Command: sudo apt install pipx python3-venv (Ubuntu Lts 22.02)
pipx install cutadapt


Tool used: TrimGalore 
Link: https://github.com/FelixKrueger/TrimGalore/blob/master/README.md
# Install TrimGalore: 
curl -fsSL https://github.com/FelixKrueger/TrimGalore/archive/0.6.10.tar.gz -o trim_galore.tar.gz
tar xvzf trim_galore.tar.gz
# Run Trim Galore
~/TrimGalore-0.6.10/trim_galore
