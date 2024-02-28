# Hybrid genome assembly combining PacBio-HiFi and Oxford Nanopore reads using Hifiasm 

1. Hifi data in circular consensu sequence (CCS) format recieved from sequencer

2. Convert CCS file into fastq (.fq) format using pacbio toolkit (pbtk) through CCS.bam to fastq package [link](https://github.com/PacificBiosciences/pbtk)

```
# bam2fastq package
# firstly index and convert CCS.bam to pbi format to .fastq

pbindex pbhifi_merged.ccs.bam
bam2fastq -o out in_1.bam in_2.bam in_4.bam
```
3. Quality control of Oxford Nanopore reads 

```
# merge all basecalled ONT fastq files

merge fastq

# filtering ONT reads less than 3kb using "Chopper package"


gunzip -c pbhifi_merged.fastq.gz | chopper -l 3000 | gzip > filtered_3kb_pbhifi_merged.fastq.gz  		# Kept 736592 reads out of 770078 reads
```

4. Hybrid genome assebly using Hifiasm
```
hifiasm -l0 --hg-size 25.5m -u 0 -o pb3A.asm -t32 --ul ont_3kb_reads.fastq.gz --hom-cov auto pb3A_hifi.fastq.gz  # l0 = to haploid input

# The FASTA file can be produced from GFA as follows:

awk '/^S/{print ">"$2;print $3}' test.p_ctg.gfa > test.p_ctg.fa
```
5. 