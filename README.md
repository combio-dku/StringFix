# StringFix: an annotation-guided transcriptome assembler

## Brief introduction
- StringFix recover transcript sequence and the corresponding amino acid sequence by taking small variants (INDEL and SNP) into account.
- It optionally utilizes a previous annotations (in GTF or GFF file format) to generate amino acid sequences while reflecting small variants found in the alignment of reads to a reference genome.
- You can use either the GTF annotation associated with the reference genome or the GFF file generated by some reference-based transcriptome assmeblers, such as [StringTie](https://github.com/gpertea/stringtie), [Cufflink](http://cole-trapnell-lab.github.io/cufflinks/), [Strawberry](https://github.com/ruolin/strawberry) and so on.
- Basically, the SW recovers amino acid sequence from the transcript sequence based on the annotations in GTF/GFF, if there is no changes in start/stop codon.
- While, if start/stop codon is garbled, it searches a new open reading frame (ORF) by applying the 'longest ORF rule'.
- cite: Lee J, Kim M, Han K, and Yoon S, StringFix: an annotation-guided transcriptome assembler improves
the recovery of amino acid sequences from RNA-Seq reads, Genes & Genimics  https://doi.org/10.1007/s13258-023-01458-7 

## Installation using pip

StringFix can be installed using pip command. With python3 installed in your system. Use the follwing command in a terminal.

`pip install StringFix`

StringFix requires the pre-installed python packages including `Numpy`, `Pandas`, `sklearn`, and `scipy`.

## Command line usage of StringFix

- `run_sfix.py` is a python script that can be run in a terminal. 
- Download `run_sfix.py` to your local directory and simply run the script by typing `python3 run_sfix.py` or `python run_sfix.py` in a terminal to see the available parameters.
- According to what information is provided, StringFix is run in one of the following modes of operation.

  1. __Genome-guided mode__: requires only SAM or BAM file (a mandatory parameter) ([pybam](https://github.com/JohnLonginotto/pybam) is used to load BAM file.)
  2. __Annotation-guided mode__: requires SAM/BAM and GTF/GFF annotation, where, for the latter, one can use either the reference GTF associated to the reference genome or the GFF file generated by some genome-guided transcriptome assemblers
  3. __Annotation-guided mode with sequence correction__: requires SAM/BAM, GTF/GFF annotation and the reference genome (The reference genome must be the one used for read alignment)

- Once it is successfully run, it outputs the following files

  1. __transcriptome.fasta__, containing the transcript sequences for all the isoforms that were detected as 'expressed' with its estimated coverage above the threshold
  2. __Expression profiles__ in 'tsv' format, containing the raw read coverage depth and TPM for all the transcript detected
  3. __SNV summary__ in 'tsv' format, containg all the small variations, including indel and SNP. SNPs are provided only if the path to the reference genome is provided
  4. __proteome.fasta__, containing the amino acid sequences for all the protein-coding genes that were detected as 'expressed' with its estimated coverage above the threshold. (Path to the reference genome must be given to get protein sequences)

## Example data and script
1. Click [here](https://drive.google.com/file/d/1GLMhaBGxPiG9--x8oMGXg9bjXORC3fRR/view?usp=sharing) to download the test data and store it to your preferred directory.
2. decompress the file by typing `tar -xzvf StringFix_test_data.tar.gz` in a terminal.
3. Change directory to the decompressed directory.
4. run `./test_run.sh`. (If needed, make the shell script executable by typing `chmod 777 test_run.sh`)

## Contact
Send email to syoon@dku.edu for any inquiry on the usages.



