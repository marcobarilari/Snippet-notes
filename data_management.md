# Data management

## Datalad

```
datalad create -c text2git mydataset

datalad clone git@gin.g-node.org:/RemiGau/V5_high-res_pilot-1_source.git

datalad siblings add --name gin --url

datalad save -m 'add mri data'

datalad push --to gin

datalad drop .
```

## Terminal

Copy a simulink files

`cp -L file fileto #grab annex content`

`chmod +w file`
