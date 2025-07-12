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
cd TrimGalore-0.6.10
Command:
./trim_galore --paired /mnt/e/GitHub_Projects/subset_1.fastq /mnt/e/GitHub_Projects/subset_1.fastq -o /mnt/e/GitHub_Projects/data/trimmed

=== Summary ===
### subset_1.fastq
Total reads processed:                 458,003
Reads with adapters:                   133,259 (29.1%)
Reads written (passing filters):       458,003 (100.0%)

Total basepairs processed:    61,641,554 bp
Quality-trimmed:                  22,254 bp (0.0%)
Total written (filtered):     61,414,492 bp (99.6%)

### subset_2.fastq
Total reads processed:                 458,003
Reads with adapters:                   230,097 (50.2%)
Reads written (passing filters):       458,003 (100.0%)

Total basepairs processed:    64,488,635 bp
Quality-trimmed:                  16,306 bp (0.0%)
Total written (filtered):     64,237,998 bp (99.6%)

# Alignment
Bismark needs the following tools to be installed and ideally available in the PATH environment:
Bowtie2: https://bowtie-bio.sourceforge.net/bowtie2/index.shtml
HISAT2: https://daehwankimlab.github.io/hisat2/
Minimap2: https://lh3.github.io/minimap2/minimap2.html
Samtools: https://www.htslib.org/download/

### Download Bowtie2 
Link: https://sourceforge.net/projects/bowtie-bio/files/bowtie2/2.5.4/bowtie2-2.5.4-source.zip/download
command: wget https://sourceforge.net/projects/bowtie-bio/files/bowtie2/2.5.4/bowtie2-2.5.4-source.zip/download
unzip bowtie2-2.5.4-source.zip
cd bowtie2-2.5.4
make
ls -l bowtie2*
export PATH=/mnt/e/GitHub_Projects/bowtie2-2.5.4:$PATH
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
cd ..
wget https://github.com/FelixKrueger/Bismark/archive/master.zip
unzip master.zip

Download Human genome for alignment
Link: https://hgdownload.soe.ucsc.edu/goldenPath/hg19/bigZips/
Human Genome: hg19.fa
gunzip hg19.fa.gz
cd Bismark-master

move the hg19.fa file into a folder say 'genome'

command: Build Bismark Index
./bismark_genome_preparation --bowtie2 /mnt/e/GitHub_Projects/genome

cd Bismark-master
Alignment command: 
bismark --genome /mnt/e/GitHub_Projects/genome/ -1 /mnt/e/GitHub_Projects/data/trimmed/subset_1_val_1.fq -2 /mnt/e/GitHub_Projects/data/trimmed/subset_2_val_2.fq -o results/

# Deduplication
Command:
deduplicate_bismark --bam results/*bismark_bt2_pe.bam

# Methylation extraction
Command:
bismark_methylation_extractor


# Sample report
Command:
bismark2report


# Summary report
Command:
bismark2summary




