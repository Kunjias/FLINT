# provision_index.py

latest commit comment from original repository:

```
Bringing the index provisioning script up to par with the latest release.

OBJECTIVE:
The purpose of this program is to copy the Bowtie2 index to all the worker nodes in the cluster in parallel, 
so that the index is not copied sequentially and takes a lot of time.

Required Dependencies:
```
- ```Apache-Spark```
- ```Python```
- ```R```

- line 24 (``` # check python modules currently installed```)
```python -c "help('modules')"```

- line 42 (``` # Spark Modules ```) \
``` from pyspark import SparkConf, SparkContext ```

- line 45-51 (``` # Python Modules ```) \
``` sys, argparse, time, collections, timedelta from datetime, subprocess as sp, shlex ```

- line 56-162 (``` # Main```)
```
def main(args):
    """
    Main function of the app.
    Args:
        args: command line arguments.
        
    Returns:
    
    """
```
- line 69-73 (add command-line arguments) \
```shards, bowtie2_index, verbose```

- line 75-76 (define ```index_location_s3``` taken from ```args.bowtie2_index```, str, with leading and trailing spaces removed)
- line 77 (define ```number_of_index_shards``` taken from ```args.shards```, int)

- line 82-90 (``` # Spark Configuration, and App declaration```)

- line 82 (set ```APP_NAME```) \
```APP_NAME = "Index_Provisioning" ```

- line 83 (create a sparkContext Object) \
``` conf = (SparkConf().setAppName(APP_NAME))```

- line 84 (set number of partitions in RDDs) \
``` conf.set("spark.default.parallelism", int(number_of_index_shards))```

- line 85 (set memory to be allocated per driver in the cluster) \
``` conf.set("spark.executor.memoryOverhead", "1G")```

- line 86 (set customize wait time to launch before moving on to a less-local node) \
``` conf.set("conf spark.locality.wait", "1s")```
- line 88-90 (convert local time to specified format, print ```Configuring Spark...```)

- line 93 (```# Initialize the Spark Context for this run.```) \
``` sc = SparkContext(conf=conf) ```

- line 95 (record time in seconds since the epoch as ```start_time```) \
`start_time = time.time()`

- line 97-100 (convert local time to specified format, print `Starting Index Copy from: `)
    - at line 99 (print `index_location_s3`, [`args.bowtie2_index` without spaces])

- line 102 (`#  Prepare the locations that will be copied.`)
- line 103 (construct an empty list of `list_of_index_shards`) \
`list_of_index_shards = []`
- line 104 (set a `range_end` number of `number_of_index_shards`+1 to loop through the shards)
    - as range function does not include the end \
`range_end = number_of_index_shards + 1`

- line 105-107 (a loop to append new index shards to `list_of_index_shards`) 
    - each new index is formed by appending bowtie2_index with partition_id in string format increasing from 1 to the number of index shards 
```
for partition_id in range(1, range_end):
    s3_location = index_location_s3 + "/" + str(partition_id)
    list_of_index_shards.append(s3_location)
```
- line 109 (printing current time to display `Index Shards to Copy:`)

```print("[ " + time.strftime('%d-%b-%Y %H:%M:%S', time.localtime()) + " ] Index Shards to Copy:")```

- line 111,112 (a loop to print out all elements of `list_of_index_shards`)
```
for location in list_of_index_shards:
    print(location)
```
- line 114 (print current time converted to desired format after printing each one of the index shards)
    - *day of month as a decimal*
    - *number-locale's abbreviated month name-year without century as a decimal number*
    - *Hour(24-hour clock) as a decimal number*
    - *Minute as a decimal number* 
    - *Second as a decimal number* 
 
```print("[ " + time.strftime('%d-%b-%Y %H:%M:%S', time.localtime()) + " ] ")```

- line 116 (create distributed dataset to be operated in parallel) \
`index_shards = sc.parallelize(list_of_index_shards)`

- line 117 (commented out,reshuffling the `index_shards` dataset) \
`# index_shards = index_shards.repartition(number_of_index_shards)`

- line 119-120 (print localtime in desired format along with number of RDD partitions in string format)
```
print("[ " + time.strftime('%d-%b-%Y %H:%M:%S', time.localtime()) + " ] No. RDD Partitions: " +
          str(index_shards.getNumPartitions()))
```

- line 122-123 (print localtime along with `Starting to copy...`)
- line 129 (` # acknowledge_RDD will dispatch the "copy_index_to_worker()" function to all the workers `)
    - `via the "mapPartitions()" function` \
`acknowledge_RDD = index_shards.mapPartitions(copy_index_to_worker)`

- line 135,136,137 \
   `acknowledge_list = acknowledge_RDD.collect()` (return elements of collected responses as an array) \
   `acknowledge_list.sort()` (sort the list of responses collected) \
   `number_of_acknowledgements = len(acknowledge_list)` (count the length of list)

- line 140-143 (Print out date-time with `No. of Workers that acknowledged`)

- line 145-147 (Condition loop to print out each acknowledgement in acknowledge_list when `args.verbose` is true)

- line 167 (```# Spark Stop, shut down the cluster once everything completes.```)
- line 170-196 (copy_index_to_worker function)
- line 204-205 (``` # Init, App Initializer ```)
- line 209 (``` # End of Line ```)
