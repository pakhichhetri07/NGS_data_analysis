## Dataset

Dataset: https://www.ncbi.nlm.nih.gov/sra/?term=ERR361748
SRA Database ID: ERR361748
Curated dataset contains two files labeled as “subset 1 (133.8 MB)” and “subset 2 (139.5 MB)”, both derived from ERR361748
Citation: Ryan, D., & Wolff, J. (2017). MethylSeq_2017 [Data set]. Zenodo. https://doi.org/10.5281/zenodo.557099

## Download dataset instruction
Visit SRA (Sequence Read Archive) database 
Link: https://www.ncbi.nlm.nih.gov/sra/
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
Command: 
sudo apt install pipx python3-venv (Ubuntu Lts 22.02)
pipx install cutadapt
cutadapt --version

Tool used: TrimGalore 
TrimGalore needs the following tools to be installed and ideally available in the PATH environment:
Install Cutadapt 
Link: https://cutadapt.readthedocs.io/en/stable/installation.html
Command: 
sudo apt install pipx python3-venv (Ubuntu Lts 22.02)
pipx install cutadapt
cutadapt --version

Link: https://github.com/FelixKrueger/TrimGalore/blob/master/README.md
# Install TrimGalore: 
curl -fsSL https://github.com/FelixKrueger/TrimGalore/archive/0.6.10.tar.gz -o trim_galore.tar.gz
tar xvzf trim_galore.tar.gz
# Run Trim Galore
~/TrimGalore-0.6.10/trim_galore
Command: ./trim_galore --paired /mnt/c/Users/Pakhi/OneDrive/Desktop/My_documents/GitHub_Projects/subset_1.fastq /mnt/c/Users/Pakhi/OneDrive/Desktop/My_documents/GitHub_Projects/subset_2.fastq -o /mnt/c/Users/Pakhi/OneDrive/Desktop/My_documents/GitHub_Projects/data/trimmed

## Alignment
Bismark needs the following tools to be installed and ideally available in the PATH environment:
Bowtie2: https://bowtie-bio.sourceforge.net/bowtie2/index.shtml
HISAT2: https://daehwankimlab.github.io/hisat2/
Minimap2: https://lh3.github.io/minimap2/minimap2.html
Samtools: https://www.htslib.org/download/

# Download Bowtie2 
Link: https://sourceforge.net/projects/bowtie-bio/files/bowtie2/2.5.4/bowtie2-2.5.4-source.zip/download
command: wget https://sourceforge.net/projects/bowtie-bio/files/bowtie2/2.5.4/bowtie2-2.5.4-source.zip/download
unzip bowtie2-2.5.4-source.zip
cd bowtie2-2.5.4
make
ls -l bowtie2*
export PATH=/mnt/c/Users/Pakhi/OneDrive/Desktop/My_documents/GitHub_Projects/bowtie2-2.5.4:$PATH
./bowtie2 --version

Download & install samtools
Link: https://www.htslib.org/download/
tar -xvjf samtools-1.22.tar.bz2
cd samtools-1.22   
./configure 
make
make install
export PATH=/mnt/c/Users/Pakhi/OneDrive/Desktop/My_documents/GitHub_Projects/samtools-1.22:$PATH
echo 'export PATH=/mnt/c/Users/Pakhi/OneDrive/Desktop/My_documents/GitHub_Projects/samtools-1.22:$PATH' >> ~/.bashrc
source ~/.bashrc

Download & install Bismark
Link: https://felixkrueger.github.io/Bismark/installation/
Documentation: https://felixkrueger.github.io/Bismark/quick_reference/
Commands:





