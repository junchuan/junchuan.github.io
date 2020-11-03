---
title: Frequently Used Docker Image/Containter Commands
date: 2020-08-24 21:29:08
categories:
  - Notes

tags:
  - docker
---

This post list commonly used docker commands.

---

## Docker image

Docker image is the nucleus for container.

- `docker image ls` : list all the images on your machine
- `docker search` : sesearch publicly avaiable docker image on Docker Hub.
- `docker pull` :  download a image from Docker registry

## Docker file

A simple text file that defines how an image should be built.

## Docker container

- Execute additional process inside an already-running container
  - `docker container exec -i -t image-name /bin/sh`

- Run a container interactively
  - `docker run -it *image-name* sh`

- Run a container in detached mode
  - `docker run -d -P --name static-site prakhar1989/static-site`
  - `-d` will detach the terminal from the container. `-P` publish all exposed ports.`-p localport:remote port` can customize the port forwarding. `--name` is the name we give to  the container
  - `docker port container-name` will list all the published ports

- Stop a detached container
  - `docker stop container-name`

- Automatically remove container when it exits
  - `docker run -rm *image-name*`

- Remove all containers that have exited
  - `docker rm $(docker ps -q -f status=exited)`
  - `docker container prune`

- Manually create image from a container
  - `docker container commit sample my-image`

- See how custom docker image was built
  - `docker image history image-name`

## Docker File Keywords

- `FROM`: define which base image this image will be based on. On Docker Hub, there are a lot of officially curated images for various OS, development frameworks etc. 
- `RUN`: any valid linux command can follow `RUN`.
- `COPY` & `ADD`: copy files or folders from host to the image. `ADD` keyword also lets us copy and unpack TAR files, as well as provide a URL as a source for the files and folders to copy.
- `WORKDIR`: define the working directory or context that is used when a container is run from the image.
- `CMD` & `ENTRYPOINT`: define what the start process is and how to start the process.

## Reference links

1. [docker for beginners](https://docker-curriculum.com/#playing-with-busybox)