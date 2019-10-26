# Answers to Multi-plexing questions

*Part 1 -1*

|Type|File|
|---|---|
|Paired-end read #1|             1294_s1_L008_R1_001.fastq.gz|
|Index #1|                       1294_s1_L008_R2_001.fastq.gz |
|Paired-end read #2|             1294_s1_L008_R4_001.fastq.gz|
|Index #2 |                      1294_s1_L008_R3_001.fastq.gz|

*Part 1-2*

a.)The histograms and the scripts used to obtain them are in separate files in this repository.  It's interesting to note that most of the low quality reads are indeed clusteres at the beginning of the read. (See Paired end read #1 -chart 2 excel file)  Also a bit over 80% of the paired end reads #1 have a quality score of 38.96 or better.  The index for the second read has much lower quality reads the first several nucleotides had mean quality scores around 35.  The second reads themself were also lower with about 75% below 38.

b.)     What constitutes a good quality score cut-off is entirely dependent on the needs and desires of the individual primary investigator.  Given that in other fields of biology, we often demand a standard error below 0.5%, I would be tempted to toss out any read with a quality score below 40, but retain those for the investigators and if they are used in any subsequent mapping, indicate what the lowest quality score used was and the percent of base pairs at quality score levels below 40.  I would like to maintain a quality score cut off that was 40 for indexes, as I'd like to be entirely sure that index hopping has not happened, that I am not using reads from other sources.
    If this data is representetive of many dual end-paired reads, the data could be very limited if my strict quality mean choices were applied.  We'd be unable to use at least 75% of the second read.  Cleaning up visible index swapping, as in part 2 of this excerices, would help.  Ultimately, many base calls will be partly cleand up in alignment and mapping. as fragments with low quality base pairs will not overlap well.  Thus, it migh be necessary and useful to drop the threshold to 17 or 35.

c.)  I used two commands to obtain this information, one for each of the paired end read files.
    zcat /projects/bgmp/shared/2017_sequencing/1294_S1_L008_R4_001.fastq.gz|awk "NR%4==2"|grep 'N'| wc -l
    zcat /projects/bgmp/shared/2017_sequencing/1294_S1_L008_R1_001.fastq.gz|awk "NR%4==2"|grep 'N'| wc -l
    The resulting answers were 3,976,613 and 3,591,851.  The total equaled  7,568,464.
