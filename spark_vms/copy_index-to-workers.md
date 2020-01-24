#copy-index-to-workers.txt

latest commit comment from original repository:
```
Virtual Machines Trial
```

transfer file to specified remote destinations (spark worker nodes)
```
scp -r . biorg@spark-worker-1:/path/to/ensembl/bowtie2/index/ensembl_v35
scp -r . biorg@spark-worker-2:/path/to/ensembl/bowtie2/index/ensembl_v35
scp -r . biorg@spark-worker-3:/path/to/ensembl/bowtie2/index/ensembl_v35
scp -r . biorg@spark-worker-4:/path/to/ensembl/bowtie2/index/ensembl_v35
```
