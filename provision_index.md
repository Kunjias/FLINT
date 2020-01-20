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

- line 93 (```# Initialize the Spark Context for this run.```)
``` sc = SparkContext(conf=conf) ```


- line 167 (```# Spark Stop, shunt down the cluster once everything completes.```)
- line 170-196 (copy_index_to_worker function)
- line 204-205 (``` # Init, App Initializer ```)
- line 209 (``` # End of Line ```)
