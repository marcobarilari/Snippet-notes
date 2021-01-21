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

```bash
singularity pull --name ~/sing_images/mriqc_0.15.2.sif docker://poldracklab/mriqc:0.15.2

singularity run --cleanenv --bind ~/mriqc_sub-pilot001_ses-001_task-visualLocalizer/raw:/data --bind ~/mriqc_sub-pilot001_ses-001_task-visualLocalizer/derivatives/mriqc:/out \
~/sing_images/mriqc_0.15.2.sif \
/data /out participant \
--participant_label pilot001
```

```bash
singularity run --cleanenv \
--bind ~/data/V5_high-res_pilot-1/raw:/data \
--bind ~/data/V5_high-res_pilot-1/derivatives/mriqc:/out \
~/sing_images/mriqc_0.15.2.sif \
/data /out participant \
--participant_label pilot001


singularity run --cleanenv docker://poldracklab/mriqc:0.15.2 \
data/V5_high-res_pilot-1/raw \
data/V5_high-res_pilot-1/derivatives/mriqc \
participant

singularity run --cleanenv /work:/work sing_images/mriqc_0.15.0.sif \
    data/V5_high-res_pilot-1/raw/ data/V5_high-res_pilot-1/derivatives/mriqc/ \
    participant


singularity run --cleanenv \
--bind ~/data/V5_high-res_pilot-1/raw:/data \
--bind ~/data/V5_high-res_pilot-1/derivatives/mriqc:/out \
--bind ~/work:/work \
~/sing_images/mriqc_0.15.2.sif \
/data /out participant \
--participant_label pilot001
```

## fMRI analysis

input_dir=/Users/barilari/data/V5_high-res_pilot-1_raw/

output_dir=/Users/barilari/data/V5_high-res_pilot-1/derivatives/mriqc/

```bash
docker run -it --rm \
-v $dataset_dir/raw:/data:ro \
-v $dataset_dir/report/mriqc:/out \
poldracklab/mriqc:0.16.0 \
/data /out --no-sub --verbose-reports participant --participant-label pilot001

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
-i nipreps/fmriprep:20.2.1 \
--verbose --participant-label pilot001 \
--fs-license-file $FREESURFER_HOME/license.txt

fmriprep-docker \
$dataset_dir/raw \
$dataset_dir/derivatives \
-i nipreps/fmriprep:20.2.1 \
--verbose --participant-label pilot001 \
--fs-license-file $FREESURFER_HOME/license.txt

docker run -ti --rm \
    -v $input_dir:/data:ro \
    -v $outputdir:/out \
    -v $$FREESURFER_HOME/license.txt \
    poldracklab/fmriprep:20.1.2 \
    /data /out/out participant --participant-label 001
```

`docker pull poldracklab/fmriprep:20.1.2`
