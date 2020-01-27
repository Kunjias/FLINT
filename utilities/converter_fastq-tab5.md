# converter-fastq-tab5.py

latest commit comment from original repository: 
``` 
Tab-5 Initial Commit.

The purpose of this file is to merge pairs of paired-end reads stored in two (2) files into one (1) single
file in "tab5" format. The tab5 format is:
    [name]\t[seq1]\t[qual1]\t[seq2]\t[qual2]\n
```

- main function taking `args` as parameter
- line 47-49 (print localtime + "Starting FASTQ to TAB5 Conversion...")
- line 51-57 (add argument)
- line 59-62 (set `filePathForMate1`, `filePathForMate2`, remove leading and trailing spaces)
- line 64-65 (set `affixForOutputFile` and `output_directory`)
- line 71-74 (check if output directory exist, if not create one)
- line 76 (set `outputFile` path)

```TAB5 Conversion```
- line 82-90 (`Read Mate 1...`)
  - iterate over Mate1 file, clean up title, create dictionary with {clean_title,\[clean_title, seq, qual\]}
- line 92-100 (`Read Mate 2...`)
  - print `Reading Mate 2...`
  - write to output file with tab delimiter, never quote value
  - iterate over Mate2 file, clean up title
  - assign `dictionaryWithMate1` to `mate_1`
  - from `mate_1`, obtain `[clean_title, seq1, qual1]`
  - write the row parameter to writer's file object as `[clean_title, seq1, qual1, seq2, qual2]`.
  
 - line 102-103 (print local time and `Done`.)
