# Data management

## Datalad

```
datalad create -c text2git mydataset

datalad clone git@gin.g-node.org:/RemiGau/V5_high-res_pilot-1_source.git

# submodules
datalad clone -d git@gin.g-node.org:/RemiGau/V5_high-res_pilot-1_source.git

datalad siblings add --name gin --url

datalad save -m 'add mri data'

datalad push --to gin

datalad drop .

datalad get .
```

## Terminal

Copy a simulink files

grab annex content:

`cp -L file file-to`

copy a folder:

`cp -L -R -f folder folder-to`

make a file 'writable'
`chmod +w file`
