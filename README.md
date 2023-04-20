# StringFix
An annotation-guided transcriptome assembler

## StringFix: Brief introduction
- StringFix recover transcript sequence and the corresponding amino acid sequence by taking small variants (INDEL and SNP) into account.
- It utilizes a previous annotations (in GTF or GFF file format) to generate amino acid sequence while reflecting small variants found in alignment to a reference genome.
- You can use either the GTF annotation associated with the reference genome or the GFF file generated by some reference-based transcriptome assmeblers, such as [StringTie](https://github.com/gpertea/stringtie), [Cufflink](http://cole-trapnell-lab.github.io/cufflinks/), [Strawberry](https://github.com/ruolin/strawberry) and so on.
- Basically, the SW recovers amino acid sequence from the transcript sequence if there is no changes in start/stop codon.
- While, if start/stop codon is garbled, it searches a new open reading frame (ORF) by applying the 'longest ORF rule'.

## Installation using pip

StringFix can be installed using pip command. With python3 installed in your system, simply use the follwing command in a terminal.

`pip install StringFix`

## Command line usage of StringFix

`HiCAT_example_py_v02.ipynb` is example code of HiCAT in Jupyter notebook, where you can see how to import and run HiCAT. For quick overveiw of the usage of HiCAT, simply click `HiCAT_example_py_v02.ipynb` above in the file list.

To run the example, download the Jupyter notebook file, maker DB in `.tsv` file and a sample single-cell RNA-Seq data with `.h5ad` extension (It is one of the data we used in our paper mentioned above). Just follow the instruction below.

1. Download all the files in ZIP format.
2. Decompress the files into a desired folder.
3. Decompress 'Melanoma_5K_rev.h5ad.zip'
4. Run jupyter notebook and open the jupyter notebook file `HiCAT_example_py_v02.ipynb`
5. You can run the codes step-by-step and can see the intermediate and final results.

To run HiCAT, you need the pre-installed python packages `Numpy`, `Pandas`, `sklearn`, `scipy`, and `sknetwork`.
`seaborn` and `matplotlib` are required only to show the results, not for the HiCAT itself.
All of them can be installed simply using `pip` command.

## Using HiCAT in R

(Installed using pip) You also can import and use HiCAT in R, for which you need the R package `reticulate`.
First, import HiCAT using the following command

`library(reticulate)`  
`mkrcnt <- import("MarkerCount.hicat")`

Then, you can call the HiCAT functions as follows.

`df_res <- mkrcnt$HiCAT( .. arguments .. )` 

The arguments to pass and the return value are the same as those in python.
R example of HiCAT is in R script `HiCAT_example.R`
Tested in linux Mint with R version 4.0.5. (numpy v1.21.1, scipy v1.7.1 without scikit-network)

## Contact
Send email to syoon@dku.edu for any inquiry on the usages.


