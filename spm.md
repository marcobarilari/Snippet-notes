## Size and dimension of ROI

- spm_summarise should be able to compute this for you. To get the number of voxels with a value of 1 (assuming 0 elsewhere):

  `spm_summarise('ROI.nii','all',@sum)`

- If you were to compare ROIs of different resolution and you need to take into account the voxel size, you can ask for an output in litres:

  `spm_summarise('ROI.nii','all','litres')`
