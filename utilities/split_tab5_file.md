# split_tab5_file.py

latest commit comment from original repository:
```
Initial commit of script for splitting a TAB5 file.

OBJECTIVE:
The purpose of this program is to split a tab-5 formatted file of DNA sequencing reads into N-number of shards.
```
- line 47-52 (write everything from buffer to terminal, print localtime + `TAB5 File Splitter`)
- line 57-59 (``` sample particulars```)
- line 64-68 (set `ouput_dir`, if path does not exist, create one)
- line 73 (set testing `limits`, shard size)
- line 78-93 (read first n-lines of input file, write them out to their own shard files)
  - print processing limit# of reads...
  - set `output_file` from `output_dir`, `sample_id`, `a_limit` (one of the shard number)
  - write from tab-5 file to csv writer file, break when `line_number` is greater than `a_limit`
  - report `csv.Error` if any
  
- line 98-101 (print localtime + `Done` + exit)
