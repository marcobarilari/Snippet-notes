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

datalad clone git@gin.g-node.org:/RemiGau/V5_high-res_pilot-1_source.git

datalad siblings add --name gin --url

datalad save -m 'add mri data'

datalad push --to gin

datalad drop .

---

copy a files

cp -L file #grab annex content

chmod +w file


## ffmpeg video recording

```bash
ffmpeg -f avfoundation -list_devices true -i ""

ffmpeg -f avfoundation -i "<screen device index>:<audio device index>" output.mkv

ffmpeg -f avfoundation -r 30 -s "1280x720" -i "2" out.mkv

ffmpeg -f avfoundation -r 30 -i "2" out.mkv
```

## Docker

```bash
docker images
```
```bash
docker rmi 'IMAGE_ID'
```

## fMRI analysis

input_dir=/Users/barilari/data/V5_high-res_pilot-1_raw/

output_dir=/Users/barilari/data/V5_high-res_pilot-1/derivatives/mriqc/

```bash
docker run -it --rm \
-v $input_dir:/data:ro \
-v $output_dir:/out \
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
$input_dir \
$output_dir \
--verbose --participant-label 01 \
--fs-license-file $FREESURFER_HOME/license.txt
```
