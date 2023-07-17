# Traefik
Traefik is an open-source Edge Router for **Docker ([[docker]])**, and **Kubernetes ([[kubernetes]])** that makes publishing your services a fun and easy experience. It receives requests on behalf of your system and finds out which components are responsible for handling them.

---
## Key Concepts

- **Entry Points**: Defines the ports where Traefik listens for incoming traffic.
- **Routers**: Match incoming requests based on criteria like domain names or paths and direct them to the appropriate services.
- **Services**: Represents the backend service to which the incoming requests will be routed.
- **Providers**: Enable Traefik to automatically discover and configure routes for services in different environments, such as Kubernetes, Docker, or file-based configuration.
- **Middlewares**: Optional components that can modify the request or response behavior for a specific route.

## Traefik Configuration

Traefik can be configured using a configuration file or through command-line arguments. Here are some commonly used configuration options:

|CONFIGURATION OPTION|DESCRIPTION|
|---|---|
|`entryPoints`|Configure the ports where Traefik listens for incoming traffic.|
|`providers`|Define the providers for dynamically discovering services and routes.|
|`http`|Configure HTTP-related settings, such as routers, services, and middlewares.|
|`tcp`|Configure TCP-related settings, such as routers and services for TCP traffic.|
|`tls`|Enable TLS configuration for securing HTTPS connections.|

## Traefik Command-Line Options

Traefik provides various command-line options for running and configuring the proxy. Here are some commonly used options:

|COMMAND-LINE OPTION|DESCRIPTION|
|---|---|
|`--configFile`|Specify the path to the configuration file.|
|`--providers`|Specify the providers to enable for dynamic service discovery.|
|`--entryPoints`|Specify the entry points for incoming traffic.|
|`--api`|Enable the Traefik API for management and monitoring.|
|`--logLevel`|Set the log level for Traefik's logging output.|

## Dynamic Service Discovery and Configuration

Traefik supports dynamic service discovery and configuration for popular container orchestration platforms and infrastructure providers. Here are some commonly used providers:

- **Docker**: Automatically discovers services and routes from Docker containers.
- **Kubernetes**: Dynamically configures routes for services in a Kubernetes cluster.
- **File**: Allows manual configuration of services and routes through a file-based configuration.

These providers enable Traefik to automatically update its routing rules as services and containers are added or removed.