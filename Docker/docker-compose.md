# Docker Compose Cheat Sheet

Docker Compose is a tool for defining and running multi-container Docker applications. It allows you to define your application's services, networks, and volumes in a single `docker-compose.yml` file and run them with a single command.

## Docker Compose Basics

COMMAND | DESCRIPTION
---|---
`docker-compose up` | Create and start containers for all services defined in the `docker-compose.yml` file
`docker-compose up -d` | Create and start containers in detached mode
`docker-compose down` | Stop and remove containers, networks, and volumes defined in the `docker-compose.yml` file
`docker-compose ps` | List running containers for services defined in the `docker-compose.yml` file
`docker-compose logs` | View output logs from containers
`docker-compose build` | Build or rebuild services defined in the `docker-compose.yml` file
`docker-compose pull` | Pull updated images for services defined in the `docker-compose.yml` file

## Service Management

COMMAND | DESCRIPTION
---|---
`docker-compose start SERVICE` | Start a specific service
`docker-compose stop SERVICE` | Stop a specific service
`docker-compose restart SERVICE` | Restart a specific service
`docker-compose scale SERVICE=NUM` | Scale a specific service to the specified number of containers

## Container and Image Management

COMMAND | DESCRIPTION
---|---
`docker-compose exec SERVICE COMMAND` | Execute a command in a running container for a specific service
`docker-compose run SERVICE COMMAND` | Run a one-time command in a new container for a specific service
`docker-compose down --volumes` | Stop and remove containers, networks, and volumes defined in the `docker-compose.yml` file, including volumes
`docker-compose rm` | Remove stopped service containers

## Environment Variables

COMMAND | DESCRIPTION
---|---
`docker-compose config` | Validate and view the composed configuration
`docker-compose config --services` | List service names defined in the `docker-compose.yml` file
`docker-compose config --volumes` | List volume names defined in the `docker-compose.yml` file

## Network Management

COMMAND | DESCRIPTION
---|---
`docker-compose network ls` | List networks defined in the `docker-compose.yml` file
`docker-compose network create NETWORK` | Create a new network
`docker-compose network rm NETWORK` | Remove a network

## Docker Compose Extensions

COMMAND | DESCRIPTION
---|---
`docker-compose -f FILE` | Specify an alternate compose file (default: `docker-compose.yml`)
`docker-compose -p PROJECT` | Specify an alternate project name (default: directory name)

