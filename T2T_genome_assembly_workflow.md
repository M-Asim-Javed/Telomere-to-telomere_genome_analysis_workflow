# Hybrid genome assembly combining PacBio-HiFi and Oxford Nanopore reads with Hifiasm 

1. Hifi data in circular consensu sequence (CCS) format recieved from sequencer

2. Convert CCS file into fastq (.fq) format using pacbio toolkit (pbtk) through CCS.bam to fastq package [link](https://github.com/PacificBiosciences/pbtk)

```
# bam2fastq package
# firstly - convert CCS.bam to pbi format to .fastq


bam2fastq -o out in_1.bam in_2.bam in_4.bam
```
3. Hybrid_assembly_using_Hifiasm