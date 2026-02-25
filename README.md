In this exercise, we investigated the quality of raw reads with FastQC (v0.11.9), assemble the reads with hifiasm, and then examined the assembly quality with Quast and BUSCO.
Two conda envs was created: "long_read_assembly" for hifiasm (v0.25.0-r726) and Quast (v5.3.0), and "busco" for BUSCO (6.0.0). 
The lineage dataset used in BUSCO is: saccharomycetes_odb10
Run time: ~13 minutes for hifiasm; ~4 minutes for BUSCO (threads=10 used for both) 

Important commands used (file paths might have been changed): 
fastqc ../BINP29_resources/SRR13577846.fastq --outdir ./1_FastQC
hifiasm -o SRR13577846.asm -t 10 ../BINP29_resources/SRR13577846.fastq.gz
python /home/inf-43-2025/miniconda3/envs/long_read_assembly/bin/quast 2_hifiasm/SRR13577846.asm.bp.p_ctg.fa -o 3_Quast/
busco -i 2_hifiasm/SRR13577846.asm.bp.p_ctg.fa -l saccharomycetes_odb10 -m geno -o 4_BUSCO/
