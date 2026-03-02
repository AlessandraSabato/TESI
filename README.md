# TESI

#!/bin/bash

#join Pre-pangenome and LCWGS derived NRR contigs for annotation
cat Partial_inputs/kept_contigs_Noorganelle_Nobacteria.fasta \
    Partial_inputs/Preliminary_Pangenome.fasta \
    > Final_Pangenome.fasta

# Script per l'annotazione delle sequenze con Helixer

apptainer run --nv --cpus 4 ~/Software/helixer-docker_helixer_v0.3.6_cuda_12.2.2-cudnn8.sif Helixer.py \
--fasta-path Final_Pangenome.fasta --lineage land_plant \
--gff-output-path Final_Pangenome.fasta.helixer.gff3
