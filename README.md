# Docker101

## Installation
- Install Docker CE. Follow instructions [here](https://docs.docker.com/install/linux/docker-ce/ubuntu/#install-docker-ce-1).
```
$ sudo apt-get remove docker docker-engine docker.io # (optional) remove older version docker
$ sudo apt-get update
$ sudo apt-get install docker-ce
$ sudo docker run hello-world # (optional) to test your installation
```
- Install nvidia-docker. Please refer to [here](https://github.com/NVIDIA/nvidia-docker).
- Add user to docker group, otherwise you need to ```sudo docker```.
```
$ sudo adduser ${USER_NAME} docker
```
- (Optional) Move image workspace. **TBU**


## Common Commands
- Build image from Dockerfile.
```
$ cd ${SOME_PLACE_WITH_A_DOCKERFILE}
$ docker build -t ${IMAGE_NAME_DEFINED_BY_YOURSELF} .
```
- List all docker images.
```
$ docker images
```
- List all containers.
```
$ docker ps -a
```
- Create a new container from an image.
```
$ docker run -it ${IMAGE_NAME or IMAGE_ID} # without nvidia
$ nvidia-docker run -it -e DISPLAY=:0 -v /tmp/.X11-unix:/tmp/.X11-unix --device /dev/nvidia0 --device /dev/nvidiactl --privileged --env="DISPLAY" ${IMAGE_NAME} # with nvidia
```
- Exit from a container (Note that this will not remove your container yet).
```
root@${CONTAINER_ID}:${ANY_PATH}# exit
```
- Resume to a container.
```
$ docker start -a -i ${CONTAINER_NAME or CONTAINER_ID}
```
- Open a new bash in a container.
```
$ docker exec -it ${CONTAINER_NAME or CONTAINER_ID} bash
```
- Save changes in a container to image
```
$ docker commit ${CONTAINER_ID} ${IMAGE_NAME}
```
- Remove a container (**Check** if your changes are saved).
```
$ docker rm ${CONTAINER_ID}
```

## Additional Commands
**TBU**
