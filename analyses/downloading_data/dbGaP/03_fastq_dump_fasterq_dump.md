# Downloading FASTQ files using fast(er)q-dump

Once you have run `prefetch` to download the SRA files, you will need to decrypt
the runs into a usable format, namely FASTQ. There are two tools for doing so,
the older `fastq-dump` and the newer `fasterq-dump`. The following
recommendations are from [Edwards Lab](https://edwards.flinders.edu.au/fastq-dump/).
Further reading can also be done from
[Bioinformatics Notebook](https://rnnh.github.io/bioinfo-notebook/docs/fastq-dump.html)
and the [fasterq-dump GitHub wiki](https://github.com/ncbi/sra-tools/wiki/HowTo:-fasterq-dump).

## fasterq-dump

```{bash}
# Recommended usage

## For a single SRA file
fasterq-dump \
--mem 1G \
--threads 8 \
--split-3 \
--skip-technical \
--print-read-nr \
--outdir output_directory_for_fastqs/ \
path_to/sra_file.sra

## For all SRA files in a directory
find folder_with_sra_files -name '*.sra' | \
xargs -n 1 \
fasterq-dump \
--mem 1G \
--threads 8 \
--split-3 \
--skip-technical \
--print-read-nr \
--outdir output_directory_for_fastqs/
```

* mem
    * How much memory is allocated to this process
* threads
    * How many threads can this process use
    * Try to set to the number of cores available (if you go over, this may slow
      the program down)
* split-3
    * Places left and right end reads into separate files, with a third file
      dedicated to unpaired reads
    * Default behavior for `fasterq-dump`
* skip-technical
    * Dump only biological reads, omitting the technical reads
        * Drops barcodes and primers
    * Default behavior for `fasterq-dump` (since `--split-3` does not include
      technical reads)
    * More information about technical reads on this 
     [Biostars thread](https://www.biostars.org/p/12047/)
* print-read-nr
    * Prints to stdout the number of spots and reads read and written
        * Matches `fastq-dump` default behavior
    * AND adds the read number (/1 and /2) to the output sequence IDs

## fastq-dump

```{bash}
fastq-dump \
--split-3 \
--skip-technical  \
--readids \
--read-filter pass \
--dumpbase \
--clip \
--outdir output_directory_for_fastqs/
```

* split-3
    * Required option, alternatives include split-files and spot-group
    * Places left and right end reads into separate files, with a third file
      dedicated to unpaired reads
* skip-technical
    * Dump only biological reads, omitting the technical reads
        * Drops barcodes and primers
* readids
    * Required option, alternatives are origfmt, helicos, defline-seq and
      defline-qual
    * Append read ID after spot ID as 'accession.spot.readid' on defline
    * For paired-end reads, the sequences are appended with .1 and .2
    * You should definitely include this if using --split-spot or --split-files
      since the split sequences will otherwise be given the same ID
    * Supposedly this option is incompatible with BWA
* read-filter pass
    * Required option, alternatives are reject, criteria and readacted
    * Only returns reads that pass filtering
* dumpbase
    * Format sequence using base space (ACTG)
* clip
    * Remove adapter sequences from reads
