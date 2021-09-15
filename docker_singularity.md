
## Singularity

```bash
singularity version
singularity help
singularity cache list -v
singularity cache clean
singularity inspect <sing-img.sif> #get metadata
singularity inspect --runscript <sing-img.sif> #tells which scripts will be run
singularity inspect -e <sing-img.sif>
singularity inspect --deffile <sing-img.sif>

singularity pull library://sylabsed/examples/lolcow
singularity run lolcow_latest.
singularity exec <sing-img.sif> <command eg `python version`> #to run binaries into singularity
singularity shell <sing-img.sif> #to enter singularity and to stuff there
  id #group information (?)
  df #disk mounted
```

### singularity

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
