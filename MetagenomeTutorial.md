#Metagenome Tutorial (CENTA 10th June)

##Getting started

Login to your VM and as before move to the Projects directory:

```
cd Projects
```

## Taxonomic profiling

Today we are going to profile using [Metaphlan2](https://bitbucket.org/biobakery/metaphlan2) which is an easy to used read 
based metagenome profiler that uses a precomputed database of genes that are unique and characteristic of particular 
taxa. It requires the read mapper [Bowtie2](http://bowtie-bio.sourceforge.net/bowtie2/index.shtml) which is preinstalled on the VM. 
We are going to test it out on some fecal samples from healthy controls and children with Crohn's from the CICRA study.

Expand out the example data directory:
```
tar -xvzf MetaTutorial.tar.gz
``` 

Inside this directory are twenty fasta files. One for each sample. Have a look at one:
```
more MetaTutorial/C1_R12.fasta
```
These actually contained trimmed forward and reverse sequences collated together. More typically you might work 
with separate fastq files.

How to count the number of reads in a fasta file?
```
grep -c ">" MetaTutorial/C1_R12.fasta
```

Then run Metaphlan2 on 8 processors making a results directory for the output first:
```
mkdir MetaphlanResults
metaphlan2.py MetaTutorial/C1_R12.fasta --input_type fasta --nproc 8 > MetaphlanResults/C1_profiled_metagenome.txt
``` 

The output simply the gives the proportion of different taxa predicted at increasing levels of resolution.
```
more MetaphlanResults/C1_profiled_metagenome.txt
```

Now we are going to run all our samples in one go. This block of code must be entered together:
```
for file in MetaTutorial/*_R12.fasta
do
    stub=${file%_R12.fasta}
    stub=${stub#MetaTutorial\/}
    echo $stub
    metaphlan2.py $file --input_type fasta --nproc 8 > MetaphlanResults/${stub}.txt
done
```
