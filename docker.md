# Guide to simple commands to use the docker

- start docker in a centOS/Linux machine

```bash
sudo service docker start
```

- make sure dicker is up an running

```bash
docker info
```

- list the docker images saved on the machine

```bash
docker images
```

- remove an image (e.g. old and unused version, they can be of huge size)

```bash
docker rmi [--force] 'IMAGE_ID' 
```

- retrieve a docker image form the docker hub

```bash
docker pull poldracklab/fmriprep:20.1.2
```
