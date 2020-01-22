# flint.py

latest commit comment from original repository:
```
Bringing the index provisioning script up to par with the latest release.

Purpose of the program: create the primary Spark driver application for the implementation 
of Flint metagenomic profilingand analysis framework.

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

