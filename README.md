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
```shell
export DOCKER_ID_USER="username"
docker login
docker tag simple_image $DOCKER_ID_USER/simple_image
docker push $DOCKER_ID_USER/simple_image
```




## Export the image to docker hub (from https://docs.docker.com/docker-cloud/builds/push-images/)

In a terminal window, set the environment variable DOCKER_ID_USER as your username in Docker Cloud.

This allows you to copy and paste the commands directly from this tutorial.
```shell
 $ export DOCKER_ID_USER="username"
 ```
If you don’t want to set this environment variable, change the examples in this tutorial to replace DOCKER_ID_USER with your Docker Cloud username.

Log in to Docker Cloud using the docker login command.
```shell
 $ docker login
 ```
This logs you in using your Docker ID, which is shared between both Docker Hub and Docker Cloud.

If you have never logged in to Docker Hub or Docker Cloud and do not have a Docker ID, running this command prompts you to create a Docker ID.

Tag your image using docker tag.

In the example below replace my_image with your image’s name, and DOCKER_ID_USER with your Docker Cloud username if needed.
```shell
 $ docker tag my_image $DOCKER_ID_USER/my_image
 ```
Push your image to Docker Hub using docker push (making the same replacements as in the previous step).
```shell
 $ docker push $DOCKER_ID_USER/my_image
 ```
Check that the image you just pushed appears in Docker Cloud.

Go to Docker Cloud and navigate to the Repositories tab and confirm that your image appears in this list.
