# Docker Networking Cheat Sheet

Docker provides various networking features to allow containers to communicate with each other and with the outside world. Here are some commands and concepts related to Docker networking.

## Network Types

COMMAND | DESCRIPTION
---|---
docker network ls | List all networks
docker network create NETWORK_NAME | Create a new network
docker network inspect NETWORK_NAME | Show detailed information about a network
docker network connect NETWORK_NAME CONTAINER_NAME | Connect a container to a network
docker network disconnect NETWORK_NAME CONTAINER_NAME | Disconnect a container from a network
docker network rm NETWORK_NAME | Remove a network

## Container Networking

COMMAND | DESCRIPTION
---|---
--network NETWORK_NAME | Specify the network for a container when running it
--hostname HOSTNAME | Set the hostname for a container
--publish HOST_PORT:CONTAINER_PORT | Publish a container's port to the host
--link CONTAINER_NAME:ALIAS | Link a container to another container (Deprecated)

## DNS Resolution

- Containers in the same network can communicate using their container names as hostnames.
- Containers can use the Docker DNS server (usually 127.0.0.11) for DNS resolution.
- To resolve external hostnames, use the DNS server configured in the Docker host or specify custom DNS servers for the container.

## Network Drivers

DRIVER | DESCRIPTION
---|---
Bridge Driver | Default driver for bridge networks. Uses docker0 bridge interface.
Host Driver | Binds container to the host's network stack.
Overlay Driver | Enables multi-host communication in swarm clusters.
Macvlan Driver | Allows containers to appear as physical devices on the network.
None Driver | No networking. Containers cannot access the network.

## Network Scopes

SCOPE | DESCRIPTION
---|---
Global Scope | Networks available across the Docker swarm.
Local Scope | Networks available only on the Docker host.
Swarm Scope | Networks created and used within a swarm.

This cheat sheet provides an overview of Docker networking concepts and commands. It covers network types, commands for managing networks, container networking options, DNS resolution, network drivers, and network scopes.

Feel free to refer to this cheat sheet for quick reference and adapt it to your specific Docker networking needs.
