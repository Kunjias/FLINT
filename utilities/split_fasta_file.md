# split_fasta_file.py

latest commit comment from original repository:
```
Initial commit of FASTA file splitter.

The purpose of this program is to split a large fasta file into a user-defined 
number of partitions so that the resulting smaller files can be indexed by a program 
such as Bowtie2, or kallisto. Note that the number of partitions must be a multiple 
of 2, since the program uses a binary-partitioning strategy.
```

[Kallisto](https://pachterlab.github.io/kallisto/about): a program for quantifying abundances of transcripts from bulk and single-cell RNA-seq data,
or more generally of target sequences using high-throughput sequencing reads.

batch_iterator function:
```
def batch_iterator(iterator, batch_size):
    """
    Returns lists of length batch_size. This is a generator function, and it returns lists of the entries from the supplied
    iterator.  Each list will have batch_size entries, although the final list may be shorter. This can be used on any
    iterator, for example to batch up SeqRecord objects from Bio.SeqIO.parse(...), or to batch. Alignment objects from
    Bio.AlignIO.parse(...), or simply lines from a file handle.
    Args:
        iterator:   Iterator object to use in the main loop.
        batch_size: The batch we wish to add to the partition file.
    Returns:
    """
```

- line 64-78 (set `entry=true`, and loop through the entry)
    - set empty list batch (`batch = []`)
    - if batch has length smaller than `batch_size`, set `entry = next(iterator)`
    - break when `entry = None`
    - append entry to batch
- line 86 (write everything in buffer to the terminal)
- line 87-89 (print localtime + `Fasta File Splitter`)
- line 92-98 (pick up command line arguments)
- line 101-105 (set variables initialized from the command line arguments)
- line 112-122 (check output_directory, create one if does not exist)
       - report `OSError` as `Ouput directory already exists...`
       
```Diagnostics```
- line 27-33 (print localtime, `File to Split`, `No. of Partitions`, `Affix`,`Version`,`Output Dir`)

```FASTA File Preprocessing```
- line 44-56 (batch size is determined by counting overall number of FASTA records
divided by user-requested number of partitions).
    - print `Counting FASTA Records...`
    - obtain `listOfRecordsInFastaFile` from `fastaFileToSplit` (from command line input file)
    - get `totalNumberOfFASTARecords` from `listOfRecordsInFastaFile`
    - print localtime and `Total No. of Records`
    - obtain `batchSizeForPartitions` by dividing `numberOfPartitions` from `totalNumberOfFASTARecords`
    - print localtime + `Batch Size`

```FASTA File Splitting```
- line 65 (print `Starting Split...`)
- line 67 (get `sizeOfFastaFile`)
- line 68 (localtime + `Size of FASTA File`)

- line 74-92 (`Split the fasta file using the batch iterator`)
    - open `fastaFileToSplit` as `record_iter`
    - line 178???
    - loop through batch iterator and batch size to create `output_directory_for_partition`
    - if `output_directory_for_partition` does not exist, make directory
    - report error as `Output Subdirectory already exists`
    - set `outputFilename`
    - write records to output file (line 89-92 ???)
       
- line 98-101 (print localtime + `"Fasta File Splitter, Done"`).
       
      
