# Answers to Multi-plexing questions

*Part 1 -1*

|Type|File|
|---|---|
|Paired-end read #1|             1294_s1_L008_R1_001.fastq.gz|
|Index #1|                       1294_s1_L008_R2_001.fastq.gz |
|Paired-end read #2|             1294_s1_L008_R4_001.fastq.gz|
|Index #2 |                      1294_s1_L008_R3_001.fastq.gz|

*Part 1-2*

a.)The histograms and the scripts used to obtain them are in separate files in this repository.

b.) What constitutes a good quality score cut-off is entirely dependent on the needs and desires of the individual primary investigator.  Given that in other fields of biology, we often demand a standard error below 0.5%, I would be tempted to toss out any read with a quality score below 40, but retain those for the investigators and if they are used in any subsequent mapping, indicate what the lowest quality score used was and the percent of base pairs at quality score levels below 40.  I would maintain a quality score cut off that was 40 for indexes, as I'd like to be entirely sure that index hopping has not happened, that I am not using reads from other sources.

c.)  I used two commands to obtain this information, one for each of the paired end read files.
    zcat /projects/bgmp/shared/2017_sequencing/1294_S1_L008_R4_001.fastq.gz|awk "NR%4==2"|grep 'N'| wc -l
    zcat /projects/bgmp/shared/2017_sequencing/1294_S1_L008_R1_001.fastq.gz|awk "NR%4==2"|grep 'N'| wc -l
    The resulting answers were 3,976,613 and 3,591,851.  The total equaled  7,568,464.
