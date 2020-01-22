# flint.py

latest commit comment from original repository:
```
Bringing the index provisioning script up to par with the latest release.

Purpose of the program: create the primary Spark driver application for the implementation 
of Flint metagenomic profiling and analysis framework.

```

- The script contains the application’s main() function
- Defines the data structures to be run in the cluster

- Settings importation
    - Spark Modules, Python Modules, Flint Modules
    
- Main function
```
def main(args): 
    """
        Main function of the app.
        Args:
            args: command line arguments.
       Returns:
        """
```
- line 79 (print Flint header)

- line 82-103 (set command line arguments)

- line 106 (parse argument and invoke action)

- line 111-112 (set JSONFile path)
- line 131-152 (open JSONFile, set path and names)

- line 155-163 (set parameters for Bowtie2)

- line 165-168 (set spark job's bowtie2 name, path, and threads)

`Annotations Parsing`

- line 175-189 （set annotation bucket and path for output reports)

- line 191 (create S3 client)

- line 192 (retrieves S3 object, decode S3 object for `annotations_file`, read data for `annotations_df`)

- line 196-201 (iterate through the data frame to create annotation_dictionary of {taxonomic_id, organism_name})

- line 203-205 (count and print the number of strains in annotations)

``` Sample Processing```

- line 214-242 (prepare aSample from arrayOfSamples, obtain sampleID, sample_format, and sample_type)

``` Properties for Streaming from a Directory ```

- line 246-257(if use_streaming_dir,define the following 
    - batch_duration
    - app_name
    - output_directory
    - stream_source_dir
    - number_of_shards)
    - report KeyError if found
    
``` Properties for Streaming from Kinesis ```

- line 260-273 (if use_streaming_kinesis, define the following
    - batch_duration
    - app_name
    - output_directory
    - stream_name
    - endpoint_url
    - region_name
    - number_of_shards
    - report KeyError if found
    
``` Properties for local processing (non-streaming)```
- define `mate_1` and `mate_2`
- report KeyError as `non_stream_key_error` if found


``` Output Files```
- line 293 (create output_file from output_directory and sampleID)
- line 294 (define output_file_name as `'abundances.txt'`)

- line 296-300 (if verbose_output)
    - print localtime + Save to Amazon S3: + `save_to_s3` (from argument input)
    - print localtime + Save to Local Filesystem +`save_to_local` (from argument input)
    
- line 302-304 (if keep_shard_profiles)
    - print localtime + Retaining individual Shard Profile

- line 306 (set default value of `s3_output_bucket`)

- line 307-309 (if save_to_s3)
    - define `s3_output_bucket=aSample['output_bucket']`
    - define output_file = output_file/output_file_name
    
 - line 311-316 (if save_to_local)
    - define `local_output_directory = output_directory + "/" + sampleID`
    - line 313-316 (if path to local_output_directory does not exist)
        - print localtime + `"Output directory does not exist. Creating..."`
        - make directory for `local_output_directory`
    - line 318-321 (if keep_shard_profiles)
        - define `local_shard_profile_output_dir = local_output_directory + "/shard_profiles"`
        - line 320-321 (if path to local_shard_profile_output_dir does not exist)
            - make directory for `local_shard_profile_output_dir`
    - line 323 (define `output_file = local_output_directory + "/" + output_file_name)
    
```#Spark```
- line 333 (Define `APP_NAME = "Flint - " + str(sampleID)`, name for label that appears in EMR and Spark dashboard output.)
- line 336-341 (setting Spark configurations)
- line 344-346 (print `Batch Duration` and `Configuring Spark`)
- line 349-354 (initialize Spark context，addPyFile from modules)
    - `'modules/spark_jobs.py'`
    - `'modules/flint_sample_downloads.py'`
    - `'modules/flint_utilities.py'`
    - `'modules/flint_bowtie2_mapping.py'`
    
- line 357 (add DNA mapping resources)
    - `'services/align_service.py'`
    
- line 361 (initialize Spark Streaming context)
    - `ssc=StreamingContext(sc,batch_duration)`
    
``` Stream from a Directory ```
- line 364-386 (if use_streaming_dir)
    - `sj.dispatch_stream_from_dir` (function from `modules/spark_jobs.py`)
    - print error e as string when ValueError is found
    
``` Stream from a Kinesis source ```
- line 390-415 (if use_streaming_kinesis)
    - `sj.dispatch_stream_from_kinesis` (function from `modules/spark_jobs.py`)
    - print error e as string when ValueError is found
    
 ``` Coalesced Output Reports ```
 - line 425-427 (print local time and `Writing Coalesced Output Reports.`)
 - line 434-437 (sort overall abundace, report with descending order with most prominent Strains on top)
 
 - line 444-453 (if gca_id in annotations_dictionary)
    - get corresponding `taxa_id` and `organism_name` from the annotations_dictionary
    - if a `gca_id` is contained in the `annotations_dictionary`:
      - add `taxa_id`, `gca_id`, `organism_name` and `OVERALL_ABUNDANCES` to the `output_list`
      - map this strain's `gca_id` to a flag
    - else:
       - add `OVERALL_ABUNDANCES` to the `output_list`
 
 - line 455-465 (if report_all)
    - loop through `gca_id` in `annotations_dictionary`
    - `if gca_id in seen_strains:`, continue for next one
    - else:
        - lookup `taxa_id` and `organism_name` from `annotations_dictionary`
        - add the `taxa_id`, `gca_id`,`organism_name` and overall_abundance level of 0 to the `output_list`

``` Local Output ```
- line 472-481 (if save_to_local)
    - line 473-475 (if verbose_output, print local time and `Saving to local filesystem...`)
    - line 477-481 (write from output_list to writer line by line)
    
``` S3 Output ```
- line 485-499 (save output file to specified S3 bucket)

```Wrap-up```
- line 504-511 (record start-time, end_time, run_time; print `Analysis Run Time` and `Complete`)

```Spark Stop```
- line 517 (shut down the cluster)

```App Initializaer```
- line 525-526
    
