# Using fmriprep and MRIqc with docker on a UNIX machine

Better to set in the terminal an absolute path to one-level-up the BIDS root in this way

```bash
#macOS
dataset_dir=one-level-up-BIDS-root

#Linux
export dataset_dir=one-level-up-BIDS-root
```

check that it worked
```bash
#macOS
$dataset_dir

#Linux
echo $dataset_dir
```



## fmriprep

### useful and optional flags

```bash
--verbose
--skip-bids-validation
--output-space anat
--fs-no-reconall
--participant-label pilot001
```

### run

```bash
fmriprep-docker \
$dataset_dir/raw \
$dataset_dir/derivatives \
-i nipreps/fmriprep:20.2.3 \
--fs-license-file $FREESURFER_HOME/license.txt \
--verbose \
--participant-label pilot001 \
--output-space anat
```

## mriqc

### useful and optional flags

### run

- single participant

```bash
docker run -it --rm \
-v $dataset_dir/raw:/data:ro \
-v $dataset_dir/derivatives:/out \
poldracklab/mriqc:0.16.1 \
/data /out --no-sub --verbose-reports \
participant --participant-label pilot001
```

- group

```bash
docker run -it --rm \
-v $input_dir:/data:ro \
-v $output_dir:/out \
poldracklab/mriqc:0.16.1 \
/data /out --no-sub --verbose-reports \
group
```

*********** OLD to tidy up ***********

https://neurostars.org/t/fmriprep-on-symlinked-bids-dataset/18025/13
