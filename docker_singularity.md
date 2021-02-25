## Docker

start docker on linux

```bash
sudo service docker start
```

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
