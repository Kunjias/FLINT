# taxIDtoLineage folder

## examples/taxtree_from_ensemblBacteria.sh

```
Example of usage get_lineage.py
Script for getting taxonomic tree from EnsemblBacteria metadata file
# Metadata could be downloaded from http://bacteria.ensembl.org/info/website/ftp/index.html
# (wget ftp://ftp.ensemblgenomes.org/pub/release-38/bacteria/species_EnsemblBacteria.txt)
```

## fetch_ncbi.py
```
Objective:
    The purpose of this script is to get taxonomic tree from given file contaning the NCBI taxID column.
```

## taxIDtoLineage.py
```
Objective:
    The purpose of this script is to get taxonomic tree:
    1) The taxIDs of input file are compared with taxonomic lineage annotations of all organisms
        (The lineage file can be downloaded through NCBItax2lin tool [1])
    2) The taxIDs that couldn't be found in lineage annotation file are fetched trough the NCBI portal
        (using the script fetch_ncbi.py)
 ```
 - dependencies:
  * fetch_ncbi.py 
  * pandas 
