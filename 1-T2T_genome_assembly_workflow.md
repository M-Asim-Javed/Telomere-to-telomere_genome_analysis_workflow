# Hybrid genome assembly combining PacBio-HiFi and Oxford Nanopore reads using Hifiasm

**1. Hifi data in circular consensu sequence (CCS) format recieved from sequencer**

**2.** **Convert CCS file into fastq (.fq) format using pacbio toolkit (pbtk) through CCS.bam to fastq package** [link](https://github.com/PacificBiosciences/pbtk)

```
# bam2fastq package
# firstly index and convert CCS.bam to pbi format to .fastq

pbindex pbhifi_smrt1.ccs.bam
bam2fastq -o out in_1.bam in_2.bam in_4.bam
```
**3. Quality control of Oxford Nanopore reads**

```
# merge all basecalled ONT fastq files

merge all fastq files

# filtering ONT reads less than 3kb using "Chopper package" 


gunzip -c pbhifi_merged.fastq.gz | chopper -l 3000 | gzip > filtered_3kb_pbhifi_merged.fastq.gz 
```

**4. Hybrid genome assebly using Hifiasm**
```
hifiasm -l0 --hg-size 25.5m -u 0 -o pb3A.asm -t32 --ul ont_3kb_reads.fastq.gz --hom-cov auto pb3A_hifi.fastq.gz  

# The FASTA file can be produced from GFA as follows:

awk '/^S/{print ">"$2;print $3}' test.p_ctg.gfa > test.p_ctg.fa
```
**Note:**  ```-l0``` flag stands for haploid/inbred genome mode


**5. Polishing of final genome assembly**
```
# Quality control  using FastQC 

fastqc -t 10 pb3A_forward_paired.fastq.gz pb3A_reverse_paired.fastq.gz  -o /pb3A_qc

# Removal of adapters using Trimmomatic

java -jar /prg/trimmomatic/0.39/trimmomatic-0.39.jar PE -threads 10 pb3A_forward_R1_paired.fastq.gz pb3A_reverse_R2_paired.fastq.gz pb3A_forward_paired.fastq.gz pb3A_forward_unpaired.fastq.gz pb3A_reverse_paired.fastq.gz pb3A_reverse_unpaired.fastq.gz ILLUMINACLIP:/adapters/adapters.fa MINLEN:50 

# Hapo_G polishing with Illumina short reads

module load bwa/0.7.13 htslib/1.8 samtools/1.13 python/3.7 hapog/1.2
/prg/hapog/1.2/hapog.py --genome hybrid_assembly_hifiasm.fa --pe1 pb3A_forward_paired.fastq.gz --pe2 pb3A_reverse_paired.fastq.gz -o hapoG -t 10 -u
```
**6. Post assembly analysis**

```
# Checking the quality of assembly

quast.py pb3A_T_T_assembly.fa reference_genome.fa -o quast_assembly_report

# Compleasm_genome completeness/BUSCO

python /home/edelab/miniconda3/pkgs/compleasm-0.2.5-pyh7cba7a3_0/site-packages/compleasm.py run -a pb3A_T_T_assembly.fasta -o output_t2t_assembly -t 30 -l eukaryota  
```
