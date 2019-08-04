
# How to install docker and docker compose
![enter image description here](https://community-cdn-digitalocean-com.global.ssl.fastly.net/assets/tutorials/images/large/12122013Docker_twitter.png?1426699613)
## Install Docker Engine - Community

![enter image description here](https://png.pngtree.com/svg/20170706/35b0fff19c.svg)

```
$ sudo apt-get update
```
```
$ sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
```
```
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```
```
$ sudo apt-get update
```
```
$ sudo apt-get install docker-ce docker-ce-cli containerd.io
```

## To test your installation
```
$ sudo docker run hello-world
```

##  Install Docker Compose

![enter image description here](https://i2.wp.com/foxutech.com/wp-content/uploads/2017/06/Docker-compose-File.png?fit=1000,390&ssl=1)

```
sudo curl -L "https://github.com/docker/compose/releases/download/1.24.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```
```
sudo chmod +x /usr/local/bin/docker-compose
```
## Test the installation
```
$ docker-compose --version
docker-compose version 1.24.1, build 1110ad01
```
# How to use docker

## How to control docker service

We can user `$ sudo service docker ${command}` or we can use `$ sudo systemctl docker ${command}` for linux distribution like readhat or centos

**Start docker**

    $ sudo service docker start

**Stop docker**

    $ sudo service docker stop

**Reload docker**

    $ sudo service docker reload

**Restart docker** 

    $ sudo service docker restart

**Get docker status**

    $ sudo service docker status

## Container status

**Working container status**
  
      $ sudo docker ps
      
**All container status**

    $ sudo docker ps -a

## Control containers

![enter image description here](https://www.networkcomputing.com/sites/default/files/styles/flexslider_full/public/Docker-Teardown-01-%28Introduction%29_0.png?itok=tQ6Djg92)

 **Attach local standard input, output, and error streams to a running container**

    $ sudo docker container attach [OPTIONS] CONTAINER

**Create a new image from a container's changes**

     $ sudo docker container commit [OPTIONS] CONTAINER [REPOSITORY[:TAG]]

 **Copy files/folders between a container and the local filesystem**
 

    $ sudo docker container cp [OPTIONS] CONTAINER:SRC_PATH DEST_PATH|-

    $ sudo docker cp [OPTIONS] SRC_PATH|- CONTAINER:DEST_PATH

  **Create a new container**         

    $ sudo docker container create [OPTIONS] IMAGE [COMMAND] [ARG...]

**Inspect changes to files or directories on a container's filesystem**      
 

     $ sudo docker container diff CONTAINER

  **Run a command in a running container**     
  

    $ sudo docker container exec [OPTIONS] CONTAINER COMMAND [ARG...]

**Export a container's filesystem as a tar archive**

    $ sudo docker container export [OPTIONS] CONTAINER

**Display detailed information on one or more containers**

    $ sudo docker container inspect [OPTIONS] CONTAINER [CONTAINER...]

**Kill one or more running containers**

    $ sudo docker container kill [OPTIONS] CONTAINER [CONTAINER...]

**Fetch the logs of a container**

    $ sudo docker container logs [OPTIONS] CONTAINER

**List containers**

    $ sudo docker container ls

**Pause all processes within one or more containers**

    $ sudo docker container pause CONTAINER [CONTAINER...]

**List port mappings or a specific mapping for the container**

    $ sudo docker container port CONTAINER [PRIVATE_PORT[/PROTO]]

**Remove all stopped containers**

    $ sudo docker container prune

**Rename a container**

    $ sudo docker container rename CONTAINER NEW_NAME

**Restart one or more containers**

    $ sudo docker container restart [OPTIONS] CONTAINER [CONTAINER...]

**Remove one or more containers**

    $ sudo docker container rm [OPTIONS] CONTAINER [CONTAINER...]

**Run a command in a new container**

    $ sudo docker container run [OPTIONS] IMAGE [COMMAND] [ARG...]

**Start one or more stopped containers**

    $ sudo docker container start [OPTIONS] CONTAINER [CONTAINER...]

**Display a live stream of container(s) resource usage statistics**

    $ sudo docker container stats

**Stop one or more running containers**

    $ sudo docker container stop [OPTIONS] CONTAINER [CONTAINER...]

**Display the running processes of a container**

    $ sudo docker container top

**Unpause all processes within one or more containers**

    $ sudo docker container unpause CONTAINER [CONTAINER...]

**Update configuration of one or more containers**

    $ sudo docker container update [OPTIONS] CONTAINER [CONTAINER...]

**Block until one or more containers stop, then print their exit codes**

    $ sudo docker container wait CONTAINER [CONTAINER...]
## Docker image
**Gets a list of downloaded image in your local registry**

    $ sudo docker images

**Download image from dockerhub registry**

    $ sudo docker pull IMAGE NAME

**Upload image into docker hub registry**

    $ sudo docker push IMAGE NAME

**Remove image from your local registry**

    $ sudo docker rmi IMAGE_NAME OR ID
## How to build docker image 
**How to build standard image into your local registry**
Requirement : 
 - Directory who contain `Dockerfile` and `entrypoint.sh`
 - `entrypoint.sh` file must be executable `$ sudo chmod +x entrypoint.sh` 
 - You have to be in the same directory that contain `Dockerfile` and `entrypoint.sh` then run the build command `$ sudo docker build -t IMAGE_NAME:TAG .`


**How to build standard image into your local registry with docker-compose**
Requirement:
- `docker-compose.yml` file
- Directory that contain build file : `Dockerfile` and `entrypoint.sh` (docker-build for example)
- `entrypoint.sh` mus be executable `$ sudo chmod +x entrypoint.sh`
- No image instruction needed in `docker-compose.yml`, and it will be replaced with build command
`image : IMAGE_NAME:TAG` will be replaced with `build : ./docker-build`
