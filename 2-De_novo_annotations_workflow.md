# De novo annotations of _P_. _brassicae_ genome assembly using BRAKER3 pipeline

1. **Repeat content prediction and soft-masking** 

Repeat content prediction along the genome assembly was performed using RepeatModeller on the Galaxy Europe platform [Link](https://usegalaxy.eu/)

The predicted repeat content was soft-masked using RepeatMasker on the Galaxy Europe platform [Link](https://usegalaxy.eu/)

2. **De novo annotations using BRAKER3**

```
singularity exec braker3.sif braker.pl --genome=genome_masked.fa --species=pb 

     --prot_seq=proteins.fa  --rnaseq_sets_ids=S001A93_ID1,S001E7A_ID2,21dpi_ID3,7dpi_ID4 \

        --rnaseq_sets_dirs=./rnaseq  --threads 20 --busco_lineage eukaryota_odb10 &> pb3a.log
```
**Paramters Note:**

 1. ```--genome=genome_masked.fa``` stands for the repeat contents masked fasta file of final genome assembly

 2. ```--species=pb```

3. ```--prot_seq=proteins.fa``` reference _Pb_ proteome file  

4. ```--rnaseq_sets_ids=S001A93_ID1,S001E7A_ID2,21dpi_ID3,7dpi_ID4``` RNA seq data of 4 time points (7, 16, 21, 26 dpi)