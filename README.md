# cfDNA_LRS

Create environment
```
conda config --add channels defaults
conda config --add channels bioconda
conda config --add channels conda-forge
conda config --set channel_priority strict

conda create -n newenvironmentname -c conda-forge -c bioconda clair3 cutesv whatshap samtools
```

Run clair3
```
MODEL_NAME="[YOUR_MODEL_NAME]"         # e.g. r941_prom_hac_g360+g422 or ont_guppy5
OUTPUT_DIR="[Output directory]"

run_clair3.sh \
  --bam_fn=input.bam \                 ## change your bam file name here
  --ref_fn=ref.fa \                    ## change your reference file name here  LSS/lss_chndr/UDP_Research/RNAseq/Indices/GRCh38.primary_assembly.genome.fa
  --threads=${THREADS} \               ## maximum threads to be used
  --platform="ont" \                   ## options: {ont,hifi,ilmn}
  --model_path="${CONDA_PREFIX}/bin/models/${MODEL_NAME}" \ 
  --output=${OUTPUT_DIR}               ## output path prefix 
```

Run cuteSV
```
cuteSV <sorted.bam> <reference.fa> <output.vcf> <work_dir> \
  --max_cluster_bias_INS 100 \
  --diff_ratio_merging_INS 0.3 \
  --max_cluster_bias_DEL 100 \
  --diff_ratio_merging_DEL 0.3
```
