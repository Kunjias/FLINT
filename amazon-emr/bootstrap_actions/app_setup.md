# app-setup.sh

latest's comment in original repository:```Removing deprecated sections.```

```
OBJECTIVE:
The purpose of this script is to copy required software into the worker nodes during an EMR deployment. The script is called when an EMR cluster is provisioned during the “Additional Options” and “Bootstrap Actions”.
```

- line 34
```
# Exit if a command exists with a non-zero exit status.
set -e

# Data and Application directories in the worker nodes.

```
Versions of tools (Bowtie, Samtools, Source_bucket)

```
# Environment Setup
echo "" >> ~/.bash_profile
echo "alias l='ls -lhF'" >> ~/.bash_profile
```
- line 61,62 \
append ```alias``` to ```~./bash_profile```, set up bash_profile

```# Cert Keys ``` (set certification for spark and aws storage)

```# Worker List ``` (copy the script that retrieves the Worker node ip addresses. Used for debugging. Change access permission to ```LOCAL_WORKER_LIST_SCRIPT```)

```# Flint Project Dir``` (create directory for dropping source code)

```# Python libs``` (install python library as part of Cluster provisioning)

```# Spark Conf ```(copy the custom Spark configuration, copy the conf from S3 into the local filesystem)
