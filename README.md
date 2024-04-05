# Telomere to telomere genome analysis of *Plasmodiophora brassicae*

Workflow for the telomere to telomere genome analysis of clubroot pathogen *Plasmodiophora brassicae*  

PacBio Hifi and Oxford Nanopore reads were utilized for hybrid genome assembly using Hifiasm.

For genome annotations, BRAKER3 pipeline was used that incorporates with GeneMark-ETP + Augustus to train the model with RNASeq and protein evidence to perform the de-novo annotation, followed by TSEBRA mediated integration of both sets to improve accuracy. [Link](https://github.com/Gaius-Augustus/BRAKER).

Singularity was used to install/execute the BRAKER3 docker container [Link](https://hub.docker.com/r/teambraker/braker3).



1. [Detailed T2T genome analysis workflow](https://github.com/M-Asim-Javed/T2T_bioinformatics_workflow/blob/main/1-T2T_genome_assembly_workflow.md)

2. [De novo annotations using BRAKER3 pipeline](https://github.com/M-Asim-Javed/T2T_bioinformatics_workflow/blob/main/2-De_novo_annotations_workflow.md)

3. [ChromoMap_R based Ideogram script](https://github.com/M-Asim-Javed/T2T_bioinformatics_workflow/blob/main/3-R_Ideogram.md)
