# Snippet-notes

## terminal macOS



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
