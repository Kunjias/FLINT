# copy_index.sh
latest's comment from original repository:
```
Initial commit of the provisioning scripts for an EMR cluster launch.

OBJECTIVE:
The purpose of this script is to copy required Bowtie2 indices into the worker nodes after an EMR deployment.
* THIS SCRIPT IS DEPRECATED. It was originally developed for testing. Value mostly for debugging *.
```

- line 35-37, 39-40, 42-44

Set ```APPS_DIR, BIODATA_DIR, INDEX_DIR ```and make ```BIODATA_DIR, INDEX_DIR```.

- line 44 ???

```LOCAL_CERT=$CERT_DIR"/"$CERT_NAME```

```# Worker Nodes``` (Set ``` WORKERS_LIST_FILE```.

- line 52
``` # Get a list of the Worker nodes IP addresses ```

- line 55
``` # Number of Worker nodes ```

- line 57 (Set ``` ENSEMBL_VERSION ```)

- line 59-108 (``` # Copy the appropriate index shards into the Worker nodes ```)
- Get worker list file, get a list of the Worker nodes IP addresses.
- Count the number of Worker nodes, copy the appropriate shards into the Worker nodes.
- Starting from Worker_count=1, print worker_count, print source_dir, print target_host and target_dir.
- Check if file exist. If not, copy from aws s3. 
- Flag the index that was already copied.

- line 93 ???

```ssh -n -i $LOCAL_CERT -o StrictHostKeyChecking=no $TARGET_HOST $COPY_COMMAND```


