# split_fasta_file.py
```
The purpose of this program is to split a large fasta file into a user-defined number of partitions so that
       the resulting smaller files can be indexed by a program such as Bowtie2, or kallisto.  Note that the number of
       partitions must be a multiple of 2, since the program uses a binary-partitioning strategy.
```
