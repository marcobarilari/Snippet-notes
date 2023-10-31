# spm

## Read and write niftis

```matlab
diretory = '/home/remi/github/bidspm/lib/CPP_ROI/atlas/yeo_7networks';
atlas = fullfile(diretory, 'space-MNI152_label-2011Yeo7Networks_desc-liberal_mask.nii');

% get nifti header
header = spm_vol(atlas);

% get atlas content
content = spm_read_vols(header);

% only select voxels with label for the roi we want
mask = content == 1;

% prepare header for the output
mask_header = header;
mask_header.fname = 'mask.nii';
 
% write mask
spm_write_vol(mask_header, mask);
```

## Size and dimension of ROI

- spm_summarise should be able to compute this for you. To get the number of voxels with a value of 1 (assuming 0 elsewhere):

  `spm_summarise('ROI.nii','all',@sum)`

- If you were to compare ROIs of different resolution and you need to take into account the voxel size, you can ask for an output in litres:

  `spm_summarise('ROI.nii','all','litres')`
