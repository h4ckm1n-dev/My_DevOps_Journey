# Docker Cheat Sheet

Docker is a set of platform-as-a-service (PaaS) products that use OS-level virtualization to deliver software in packages called containers. This cheat sheet provides an overview of commonly used Docker commands and concepts.

## Installation

- Visit the [Docker homepage](https://www.docker.com/) and follow the instructions for your operating system to install Docker.

## Build Images

- Use a `Dockerfile` to define the steps to build an image.
- Build an image: `docker build -t IMAGE_NAME PATH_TO_DOCKERFILE`.
- List existing images: `docker images`.
- Remove an image: `docker rmi IMAGE_NAME`.

## Docker CLI

### Run Containers

COMMAND | DESCRIPTION
---|---
`docker run IMAGE` | Start a new container.
`docker run --name CONTAINER IMAGE` | Start a new container and set a name.
`docker run -p HOSTPORT:CONTAINERPORT IMAGE` | Start a new container with mapped ports.
`docker run -P IMAGE` | Start a new container and map all ports.

### Container Management

COMMAND | DESCRIPTION
---|---
`docker create IMAGE` | Create a new container.
`docker start CONTAINER` | Start a container.
`docker stop CONTAINER` | Gracefully stop a container.
`docker kill CONTAINER` | Forcefully kill a container.
`docker restart CONTAINER` | Restart a container.
`docker pause CONTAINER` | Suspend a container.
`docker unpause CONTAINER` | Resume a container.
`docker rm CONTAINER` | Destroy a container.

### Container Bulk Management

COMMAND | DESCRIPTION
---|---
`docker stop $(docker ps -q)` | Stop all running containers.
`docker kill $(docker ps -q)` | Kill all running containers.
`docker restart $(docker ps -q)` | Restart all running containers.
`docker rm $(docker ps -q)` | Delete all running containers.
`docker pause $(docker ps -q)` | Pause all running containers.
`docker start $(docker ps -a -q)` | Start all stopped containers.
`docker rm -vf $(docker ps -a -q)` | Delete all containers including volumes.
`docker rmi -f $(docker images -a -q)` | Delete all images.
`docker system prune` | Delete all dangling and unused images, containers, cache, and volumes.
`docker system prune -a` | Delete all used and unused images.
`docker system prune --volumes` | Delete all Docker volumes.

### Inspect Containers

COMMAND | DESCRIPTION
---|---
`docker ps` | List running containers.
`docker ps -a` | List all containers, including stopped.
`docker logs CONTAINER` | Show a container's output.
`docker top CONTAINER` | List the processes running in a container.
`docker diff CONTAINER` | Show the differences with the image.
`docker inspect CONTAINER` | Show information of a container.

### Run Commands

COMMAND | DESCRIPTION
---|---
`docker attach CONTAINER` | Attach to a container.
`docker cp CONTAINER:PATH HOSTPATH` | Copy files from the container.
`docker cp HOSTPATH CONTAINER:PATH` | Copy files into the container.
`docker export CONTAINER` | Export the content of the container.
`docker exec CONTAINER COMMAND` | Run a command inside a container.
`docker exec -it CONTAINER /bin/bash` | Open an interactive shell inside a container.
`docker wait CONTAINER` | Wait until the container terminates and return the exit code.

### Images

COMMAND | DESCRIPTION
---|---
`docker images` | List all local images.
`docker history IMAGE` | Show the image history.
`docker inspect IMAGE` | Show information about an image.
`docker tag IMAGE TAG` | Tag an image.
`docker commit CONTAINER IMAGE` | Create an image from a container.
`docker import URL` | Create an image from a tarball.
`docker rmi IMAGE` | Delete images.
`docker pull REPO:TAG` | Pull an image from a registry.
`docker push REPO:TAG` | Push an image to a registry.
`docker search TEXT` | Search for an image on the official registry.
`docker login` | Login to a registry.
`docker logout` | Logout from a registry.
`docker save REPO:TAG` | Export an image as a tarball.
`docker load` | Load images from a tarball.

### Volumes

COMMAND | DESCRIPTION
---|---
`docker volume ls` | List all volumes.
`docker volume create VOLUME` | Create a volume.
`docker volume inspect VOLUME` | Show information about a volume.
`docker volume rm VOLUME` | Delete a volume.
`docker volume ls --filter="dangling=true"` | List dangling volumes (not referenced by any container).
`docker volume prune` | Delete all volumes not referenced by any container.

## Networks

## Troubleshooting

### Networking

- Run the following command to troubleshoot networking:
```bash
docker run --name netshoot --rm -it nicolaka/netshoot /bin/bash
```