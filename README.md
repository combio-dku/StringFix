# StringFix
An annotation-guided transcriptome assembler

## StringFix: Brief introduction
- StringFix recover transcript sequence and the corresponding amino acid sequence by taking small variants (INDEL and SNP) into account.
- It optionally utilizes a previous annotations (in GTF or GFF file format) to generate amino acid sequences while reflecting small variants found in the alignment of reads to a reference genome.
- You can use either the GTF annotation associated with the reference genome or the GFF file generated by some reference-based transcriptome assmeblers, such as [StringTie](https://github.com/gpertea/stringtie), [Cufflink](http://cole-trapnell-lab.github.io/cufflinks/), [Strawberry](https://github.com/ruolin/strawberry) and so on.
- Basically, the SW recovers amino acid sequence from the transcript sequence if there is no changes in start/stop codon.
- While, if start/stop codon is garbled, it searches a new open reading frame (ORF) by applying the 'longest ORF rule'.

## Installation using pip

StringFix can be installed using pip command. With python3 installed in your system, simply use the follwing command in a terminal.

`pip install StringFix`

## Command line usage of StringFix

- `run_sfix.py` is a python script that can be run in a terminal. 
- Download `run_sfix.py` to your local directory and simply run the script by typing `python3 run_sfix.py` or `python run_sfix.py` in a terminal to see the available parameters.
- According to what information is provided, StringFix is run in one of the following 2 modes of operation.

  1. Genome-guided mode: requires only SAM or BAM file (a mandatory parameter)
  2. Annotation guided mode: requires SAM/BAM and GTF/GFF annotation, where, for the latter, one can use either the reference GTF associated to the reference genome or the GFF file generated by some genome-guided transcriptome assemblers
  3. Annotation guided mode with SNP correction: requires SAM/BAM, GTF/GFF annotation and the reference genome (The reference genome must be the one used for read alignment)

- Once it is successfully run, it outputs the following files

  1. __transcriptome.fasta__, containing the transcript sequences for all the isoforms that were detected as 'expressed' with its estimated coverage above the threshold
  2. __Expression profiles__ in 'tsv' format, containing the raw read coverage depth and TPM for all the transcript detected
  3. __SNV summary__ in 'tsv' format, containg all the small variations, including indel and SNP. SNPs are provided only if the path to the reference genome is provided
  4. __proteome.fasta__, containing the amino acid sequences for all the protein-coding genes that were detected as 'expressed' with its estimated coverage above the threshold. (Path to the reference genome must be given)

## Contact
Send email to syoon@dku.edu for any inquiry on the usages.


