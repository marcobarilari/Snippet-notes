# Docker-Singularity tools

## mriqc

```bash

singularity run --cleanenv \
--bind data/V5_high-res_pilot-1/raw:/data \
--bind data/V5_high-res_pilot-1/derivatives/mriqc:/out \
~/sing_images/mriqc_0.15.2.sif \
/data /out participant \
--participant_label pilot001 --no-sub

singularity run --cleanenv \
$HOME/data/V5_high-res_pilot-1/raw:/data \
$HOME/data/V5_high-res_pilot-1/derivatives/mriqc:/out \
$HOME/sing_images/mriqc_0.15.2.sif \
/data /out participant \
--participant_label pilot001 --no-sub

```

## fMRI analysis

input_dir=/Users/barilari/data/V5_high-res_pilot-1_raw/

output_dir=/Users/barilari/data/V5_high-res_pilot-1/derivatives/mriqc/

```bash
docker run -it --rm \
-v $dataset_dir/raw:/data:ro \
-v $dataset_dir/report/mriqc:/out \
poldracklab/mriqc:0.15.2 \
/data /out --no-sub --verbose-reports participant --participant-label pilot001

docker run -it --rm \
-v $input_dir:/data:ro \
-v $output_dir/mriqc:/out \
poldracklab/mriqc:0.15.2 \
/data /out --no-sub --verbose-reports participant --participant-label 001

docker run -it --rm \
-v $input_dir:/data:ro \
-v $output_dir:/out \
poldracklab/mriqc:latest \
/data /out --no-sub --verbose-reports group
```

```bash
fmriprep-docker \
$dataset_dir/raw \
$dataset_dir/derivatives \
-i poldracklab/fmriprep:20.1.2 \
--verbose --participant-label 01 \
--fs-license-file $FREESURFER_HOME/license.txt

docker run -ti --rm \
    -v $input_dir:/data:ro \
    -v $outputdir:/out \
    -v $$FREESURFER_HOME/license.txt \
    poldracklab/fmriprep:20.1.2 \
    /data /out/out participant --participant-label 001
```

`docker pull poldracklab/fmriprep:20.1.2`
