---
layout: blog
topic: DevOp
title: Docker
tags: devop docker 
comments: true
date: 2022-10-04
---

# Docker

## Basic concepts

- `Image`: an app to run; the build step
- `Registry`: to distribute the app; the ship step
- `Container`: an instance of the app running; the runn step


## Common command

```shell
docker version # check if docker is running
docker info # more detailed config 
docker # help
docker login
docker logout

docker container run -de --name <name> -port <80:80>
docker container ls # list running containers
docker container ls -a # list all current and past containers
docker container rm <first 3 digits of container ID> #remove containers
docker container rm -f <first 3 digits of container ID> #remove a running container
docker container prune #remove any orphan container instances.
docker image prune #remove unused images.
docker network prune #remove orphan network objects.

docker network ls
docker image ls

docker-compose up

docker container prune - remove any orphan container instances.
docker image prune - remove unused images.
docker network prune - remove orphan network objects.

```

## Processes

1. Clone the Repo
2. In the terminal, run `docker-compose up`
3. Run `devcontainer up`