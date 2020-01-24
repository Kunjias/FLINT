# deploy_index.sh

latest's commit update from the original repository:
```
Fixing the missing example for deploying an index into a cluster

OBJECTIVE:
The purpose of this script is to act as a basic driver of the index provisioning script.
```

- line 28-30 (Print date-time in month-day-year, hour-minute-second format and ``` Starting Test... ```)

- line 33, 35 (```# Base location for the project ```)

- line 38, 40 (``` # The S3 path to where the partitioned index is located at ```)

``` Configuration for Spark Cluster particulars ```

- line 48 (``` # in YARN mode, the ResourceManager's address is picked up from Hadoop configuration, --master parameter set to 'yarn'```)

- line 51 (``` # Amount of memory to allocate for the driver process.```)

- line 54 (``` # The number of cores that the Driver process will use.```)

- line 57 (``` # The number of Executor processes to launch in each Worker node.```)

- line 60 (``` # The number of cores that each Executor process will use.```)

- line 63 (``` # Amount of memory to allocate for the executor processes.```)

- line 66, 68, 70 (``` # The YARN queue in which the job will run on.```)

- line 79-88 (``` # Submit the script to the Spark cluster using "bin/spark-submit".```)

- line 91-94 (Print date-time and ```Test Finished.```)
