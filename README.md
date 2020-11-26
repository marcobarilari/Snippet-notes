# Snippet-notes

## terminal macOS

### .bash_profile

```bash_profile
alias matlab='open /Applications/MATLAB_R2017b.app'
alias rstudio='open /Applications/RStudio.app'
alias matlabter='/Applications/MATLAB_R2017b.app/bin/matlab -nodesktop -nosplash $*'

export PATH=$PATH:/Users/barilari/Library/Python/3.7/bin
export FREESURFER_HOME=/Applications/freesurfer
export FS_LICENSE=$FREESURFER_HOME/license.txt

# FSL Setup
FSLDIR=/usr/local/fsl
PATH=${FSLDIR}/bin:${PATH}
export FSLDIR PATH
. ${FSLDIR}/etc/fslconf/fsl.sh

# GitHub patch for autocomplition
if [ -f ~/.git-completion.bash ]; then
  . ~/.git-completion.bash
fi
```

## miss_hit (here)[https://github.com/florianschanda/miss_hit]

To analyse one or more files:

```bash
mh_style my_file.m
```

It is possible to also style-check and fix code embedded inside Simulink® models. To do you need to use a special command-line flag. Once the feature is stable enough, this flag will be removed.

```bash
mh_style --fix initEnv.m
```

To analyse all files in a directory tree:
```bash
mh_style src/
```

## datalad

```
datalad create -c text2git mydataset

datalad clone git@gin.g-node.org:/RemiGau/V5_high-res_pilot-1_source.git

datalad siblings add --name gin --url

datalad save -m 'add mri data'

datalad push --to gin

datalad drop .
```
---



---

copy a files

cp -L file fileto #grab annex content

chmod +w file


## ffmpeg video recording

```bash
ffmpeg -f avfoundation -list_devices true -i ""

ffmpeg -f avfoundation -i "<screen device index>:<audio device index>" output.mkv

ffmpeg -f avfoundation -r 30 -s "1280x720" -i "2" out.mkv

ffmpeg -f avfoundation -r 30 -i "2" out.mkv
```

## Terminal

```bash
ls -lrt
du -h lolcow_latest.sif #print the size
pip list
```

## Docker

```bash
docker images
```
```bash
docker rmi 'IMAGE_ID'
```

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

###mriqc

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
