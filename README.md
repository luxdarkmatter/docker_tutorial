# Docker / Shifter tutorial for LUX/LZ analysis


## Prerequist:

- Install docker on you laptop: http://docker.com
- An account on PDSF/CORI
- An account on https://hub.docker.com


## Simple image

Simple docker commands for thesimple image container building.

### Build the image

In the directory `docker_tutorial/Simple_Image`, run:
```shell
docker build -t  simple_image .
```

### Create the container

Anywhere in you computer, run:
```shell
docker run -d --name  simple_container simple_image
```

### Run the container
Anywhere in you computer, run:
```shell
docker exec -i -t  simple_container /bin/bash
```
### Export the image to docker hub
Documentation from  https://docs.docker.com/docker-cloud/builds/push-images/
Anywhere in you computer, run:

```shell
export DOCKER_ID_USER="username"
docker login
docker tag simple_image $DOCKER_ID_USER/simple_image
docker push $DOCKER_ID_USER/simple_image
```


### Import the image from docker hub to NERSC
On cori, run:
```shell
shifterimg -v pull docker:<username>/simple_image:latest
```
(chage <username> by your docker hub username)

### Check the image export on cori
On cori, run:
```shell
shifterimg images | grep simple_image
```

### Execute the image:
On cori, run:
```shell
shifter --image=<username>/simple_image <cmd>
```
Replace `<cmd>` by any commad that you want to execute inside the image, it can be a bash script, an executable... If you want to start a bash session replace it by `/bin/bash`.

The variable `SHIFTER_RUNTIME` tells you if you are inside an image or not
