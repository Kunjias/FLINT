# make_scripts.sh

```
#   OBJECTIVE:
#	The purpose of this script is to create the necessary partition indexing scripts for the High Performance Cluster.  
#	The Cluster runs the LSF scheduler, so the scripts created will have the necessary bsub submission
#	headers.
```

- Starting Script Factory
- line 39-44 (Set up `BASE_DIR, OUTPUT_PATH, make directory, `TEMPLATE_SCRIPT_PATH`)
- line 50-59 (set `ARRAY_OF_PARTITIONS`, create scripts for `PARTITION`)
- line 65-87 (create 'n' necessary indexing scripts)
- line 94-97 (Done)
