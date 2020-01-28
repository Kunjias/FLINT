1. download-scripts
  - download_ensembl_bacteria.sh 
  - Download collection of genome FASTA files from the Ensembl Bacteria project website
  - ("http://bacteria.ensembl.org")
  
2. fasta_extraction
  - expand_genomes_ensembl.sh
  - expand a collection of genome files downloaded from the Ensembl Bacteria project website 
  - ("http://bacteria.ensembl.org")
  - The compressed files are in GZip format (.gz) and the gunzip utility is used to expand these.
  
3. annotations
  - ensembl_postprocessing_python
  	- add_length_to_annotation
	- add_strain_column
	1) Add strain column to Ensembl lineage annotation file by merging lineage file with metadata from GenBank
	2) Remove first word from the species name (redundant information - represent genus)
  - ensembl_lineage.sh
  	1) Download metadata on the genomes provided by Ensembl Genomes.
      	2) Metadate could be found on http://bacteria.ensembl.org/info/website/ftp/index.html
    	3) Create phylogenetic tree for all genomes in Ensembl database
  - ensembl_postprocessing.sh
      1) Adding the correct strain name column and remove the first word from the species name 
        (redundant information - represent genus)
      2) Calculate the length of each genome and add corresponding column to annotation file
  - gb_full_annotations.sh
      - Create lineage annotations for GB full database using summary file containing tax_id column
      
      
4.fasta_concatenation
  - concatenate.py
    - concatenate a collection of genome files downloaded from the Ensembl Bacteria project website
     - ("http://bacteria.ensembl.org")
    - The files to concatenate are FASTA files for each genome, and the result will be one large FASTA file with all the sequences in them.
    
    1)	Clean the sequence headers of the FASTA files in the Ensembl Genome Index.
 	    The sequence headers in their initial format are useless for mapping purposes as they do not have a format
 	    that can be easily parsed by the Reducer steps in the main Flint MapReduce pipeline.
 	2)	Create annotation file with all sequence headers.

5. partitioning
  - create_partitions_ensembl.sh
    - act as a basic test for the 'split_fasta_file.py' utility.
  - split_fasta_file.py
    -  The purpose of this program is to split a large fasta file into a user-defined number of partitions so that
       the resulting smaller files can be indexed by a program such as Bowtie2, or kallisto.  Note that the number of
       partitions must be a multiple of 2, since the program uses a binary-partitioning strategy.

6. indexing
- index_partitions_ensembl.sh
  - The purpose of this script is to index a collection of bacterial genomes stored in a fasta file with the
  	bowtie2-build index builder program.
  
7. show_statistics
- get_statistics.py
  - The purpose of this script is to index a collection of bacterial genomes stored in a fasta file with the
	  bowtie2-build index builder program.
- run_get_statistics.sh
  
  
8. taxIDtoLineage  
The script for extending input file with a taxonomic tree.

9. configuration file
  
