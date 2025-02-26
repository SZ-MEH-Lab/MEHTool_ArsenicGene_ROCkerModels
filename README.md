# MEHTool_ArsenicGene_ROCkerModels
This repository contains As-related gene databases and ROCker models, including aioA, arxA, arrA, arsC1, arsC2, arsM, arsI, and arsP genes. If you have any other questions or needs related to the ROCker models, please don't hesitate to contact us (syzhang@des.ecnu.edu.cn). The databases and ROCker models provided here may only be used for academic exchange and are not permitted for commercial use.

If you use the databases or ROCker models of aioA, arxA, arrA, arsC1, and arsC2 genes, please cite the paper at Microbiome (https://doi.org/10.1186/s40168-024-01952-4).
If you use the databases or ROCker models of arsM, arsI, and arsP genes, please cite the paper at Environ Sci Technol (https://doi.org/10.1021/acs.est.4c08620).

Citation
Zhao, XD., Gao, ZY., Peng, JJ. et al. Various microbial taxa couple arsenic transformation to nitrogen and carbon cycling in paddy soils. Microbiome 12, 238 (2024).
Gao, ZY., Zhao, XD., Chen, Chuan. et al. Paddy Soil Flooding and Nonflooding Affect the Transcriptional Activity of Arsenic Methylation and Demethylation Communities. Environ Sci Technol (2025).

#Usage
Setp1: Execute ROCker search. The minimum required parameters are:
$> singularity exec ROCker.sif ROCker search -q input.fasta -k model.rocker -o output.blast 
Where input.fasta is the input metagenome in FastA format, model.rocker is the ROCker model(eg. ), and output.blast is the output file to be created in tabular BLAST format. For additional supported options, execute singularity exec ROCker.sifROCker search -h. (Please install ROCker.sif before use according to http://enve-omics.ce.gatech.edu/rocker/) 

#Note: If you have a pre-computed BLAST file, you can execute Setp2 directly.

Setp2:  Execute ROCker filter.

$> ROCker filter -x input.blast -k model.rocker -o output.blast 
Where input.blast is the input search to be filtered in tabular BLAST format, model.rocker is the ROCker model, and output.blast is the output file to be created in tabular BLAST format. For additional supported options, execute ROCker filter -h.

gene=aioA/arxA/arrA/arsC1/arsC2/arsM/arsI/arsP
ROCker=$gene.150.rocker.txt (the ROCker file)
input=$SAMPLE.$gene.blastout (the blastout file against the corresponding gene database)

Run
singularity exec ~/shared/apps/ROCker.sif ROCker filter -k $ROCker -x $input -o $SAMPLE.$gene.ROCker 

# If you want to know more infomation about ROCker, please see https://doi.org/10.1093/nar/gkw900.
