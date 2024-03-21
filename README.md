# Telomere to telomere genome assembly of *Plasmodiophora brassicae*

Bioinformatics workflow and script for the telomere to telomere genomic analysis of clubroot pathogen *Plasmodiophora brassicae*  

PacBio Hifi and Oxford Nanopore reads are being utilized for hybrid genome assembly using Hifiasm. For genome annotations, BRAKER3 pipeline that uses GeneMark-ETP + Augustus to train the model with RNASeq and protein evidence to perform the de-novo annotation, followed by TSEBRA mediated integration of both sets. [Link](https://github.com/Gaius-Augustus/BRAKER).

singularity was used to install/execute the BRAKER3 docker container [Link](https://hub.docker.com/r/teambraker/braker3).



1. [Detailed T2T genome analysis workflow](https://github.com/M-Asim-Javed/T2T_bioinformatics_workflow/blob/main/1-T2T_genome_assembly_workflow.md)

2. [De novo annotations using BRAKER3 pipeline](https://github.com/M-Asim-Javed/T2T_bioinformatics_workflow/blob/main/2-De_novo_annotations_workflow.md)

3. [ChromoMap_R based Ideogram script](https://github.com/M-Asim-Javed/T2T_bioinformatics_workflow/blob/main/3-R_Ideogram.md)
