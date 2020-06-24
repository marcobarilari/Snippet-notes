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

```bash
docker run -it --rm \
-v /Users/barilari/data/tutorial_Andy-Brain-Book/ds000102-download/raw/:/data:ro \
-v /Users/barilari/data/tutorial_Andy-Brain-Book/ds000102-download/derivatives/mriqc/:/out \
poldracklab/mriqc:latest \
/data /out --no-sub --verbose-reports participant --participant-label 01

docker run -it --rm \
-v /Users/barilari/data/tutorial_Andy-Brain-Book/ds000102-download/raw/:/data:ro \
-v /Users/barilari/data/tutorial_Andy-Brain-Book/ds000102-download/derivatives/mriqc/:/out \
poldracklab/mriqc:latest \
/data /out --no-sub --verbose-reports group
```

```bash
fmriprep-docker \
/Users/barilari/data/tutorial_Andy-Brain-Book/ds000102-download/raw \
/Users/barilari/data/tutorial_Andy-Brain-Book/ds000102-download/derivatives \
--verbose --participant-label 01 \
--fs-license-file $FREESURFER_HOME/license.txt
```
