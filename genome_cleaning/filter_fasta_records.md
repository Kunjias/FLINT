# filter_fasta_records.py

latest comment from the original repository

```
Genome cleaning initial commit.

OBJECTIVE:
The Purpose of this program is to filter the Ensembl Bacterial Genome database for "complete" genome records.
The majority of the genomes in Ensembl Bacteria are "SuperContig" chromosomes, or "draft" genomes that have not been completed and contain gaps. 
This filter removes those genomes and retains only "finished" genomes, or those genomes that for all intents and purposes are considered completed. 
Specifically, genomes that have a "dna:chromosome" attribute are kept, and others (dna:plasmid, and dna:supercontig are discarded.
Note that purpose of thses finished genomes are not for use in a production environment.)
```
Check python modules to ensure dependencies are installed (- BioPython).

- line 45-50 (```# Python Modules (standard)```)
- line 52-53 ???

``` Main ```
- line 61-66,68-71,73-74 (```# Pick up the command line arguments```)
- line 73-74 ???

``` Output Files & Directories ```
- line 81-85 (``` # Check if the ouput directory exists -either the current or the requested one)

``` Filter ```
- line 94-114 (``` Filter file containing the record of interest)
- line 104-108 (Loop for storing ```Assembly ID so we can look it up later on```)

```File loading```
-line 119-131


``` End of Line```
- line 136 (Print date-time and ```"Done."```)
- line 138 (exit)
