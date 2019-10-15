# SuperReads_RNA
This package is aimed at creating super-reads for Illumina RNAseq reads.  The super-reads reduce the Illumina RNAseq reads to minimal coverage set. preserving all information contained the the reads.

# Installation
To install the package, download the .tar.gz tarball from the releases tab, unzip/untar with tar -xv.  Then cd to the folder created and run ./install.sh

# Usage
The install script creates a sample configuration file sr_config_example.txt in the installation folder.  Copy this file to the location where the code will be run and edit it. The parameters are explained in the comments.  Do not worry about JF_SIZE -- it will be set automatically.  The only important setting there is NUM_THREADS for how many threads you wish to run. In the DATA section, input the names of your Illumina paired end RNAseq read files as follows:
PE= <two character prefix> <estimated library mean> <estimated library stdev> <forward_reads.fastq(.gz)> <reverse_reads.fastq(.gz)>
  
if library mean/stdev is not known, use 500 and 50.  For single-ended reads omit the reverse reads file.  Fastq files may be gzipped.

To run the super-reads execute

/installation path/bin/createSuperReads_RNA <config_file>

This will create an assemble.sh script.  Run this script.  If you already have an incomplete run in the current folder, re-run createSuperReads_RNA and it will create an updated assemble.sh script, omitting the commands that ran successfully.

The super-reads are output in work1/superReadSequences.fasta
The read positions in the super-reads are in work1/readPlacementsInSuperReads.final.read.superRead.offset.ori.txt

