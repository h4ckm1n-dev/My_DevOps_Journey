[Rancher Official Website](https://rancher.com/)

Rancher is an open-source container management platform that simplifies the deployment and management of containerized applications in production environments. It provides a user-friendly interface and powerful orchestration capabilities to manage containers and Kubernetes clusters across different cloud providers or on-premises infrastructure.

Key features of Rancher include:

1. Multi-Cluster Management: Rancher allows you to manage multiple Kubernetes clusters from a single centralized interface. You can easily provision, upgrade, and scale clusters across different cloud providers or on-premises infrastructure.
    
2. Kubernetes as a Service: Rancher provides a streamlined experience for deploying and managing Kubernetes clusters. It abstracts away the complexities of cluster setup and configuration, making it easy to deploy production-ready Kubernetes clusters with just a few clicks.
    
3. Application Catalog: Rancher offers an application catalog with a wide range of pre-configured templates for deploying popular containerized applications. It simplifies the process of deploying complex application stacks and reduces the time required for setup and configuration.
    
4. User Management and RBAC: Rancher includes built-in user management and role-based access control (RBAC) capabilities. You can create and manage user accounts, define roles and permissions, and control access to resources within the Rancher environment.
    
5. Monitoring and Logging: Rancher integrates with various monitoring and logging solutions, allowing you to collect and analyze metrics and logs from your containers and Kubernetes clusters. It provides visibility into the health and performance of your applications and infrastructure.
    
6. Load Balancing and Service Discovery: Rancher includes built-in load balancing capabilities to distribute traffic across containers and services. It also offers service discovery mechanisms to dynamically update DNS records and enable seamless communication between services.
    
7. Infrastructure Provisioning: Rancher supports multiple infrastructure providers, including major cloud providers like AWS, Azure, and Google Cloud Platform, as well as on-premises infrastructure. It allows you to provision and manage the underlying infrastructure resources required for running containers and Kubernetes clusters.
    
8. Extensibility and Integration: Rancher provides an open and extensible platform with a rich set of APIs and integrations. It enables you to automate workflows, integrate with external systems, and extend the functionality of Rancher to suit your specific requirements.
    

Rancher is designed to simplify the entire containerization lifecycle, from cluster deployment to application management and monitoring. It offers a comprehensive set of tools and features that make it easier for teams to adopt and manage container technologies in production environments.

## Key Concepts

- **Cluster**: A group of nodes that work together to run containerized applications.
- **Node**: A physical or virtual machine that is part of a cluster and can host containers.
- **Workload**: A containerized application or set of applications running on a node.
- **Project**: A logical grouping of workloads within a cluster, often used to organize applications or teams.
- **Stack**: A collection of services, volumes, and networks that define an application or microservice architecture.
- **Service**: A component of a stack that represents a running container or group of containers.

## Rancher CLI (rancher CLI)

The Rancher CLI allows you to interact with Rancher from the command line. Here are some commonly used commands:

|COMMAND|DESCRIPTION|
|---|---|
|`rancher login <RANCHER_URL>`|Log in to a Rancher server|
|`rancher context switch <CONTEXT_NAME>`|Switch to a different Rancher context|
|`rancher cluster ls`|List clusters|
|`rancher cluster create`|Create a new cluster|
|`rancher cluster delete <CLUSTER_ID>`|Delete a cluster|
|`rancher node ls`|List nodes in a cluster|
|`rancher node add <CLUSTER_ID>`|Add a new node to a cluster|
|`rancher node remove <NODE_ID>`|Remove a node from a cluster|
|`rancher project ls`|List projects in a cluster|
|`rancher stack ls`|List stacks in a project|
|`rancher stack create`|Create a new stack in a project|
|`rancher stack delete <STACK_ID>`|Delete a stack|
|`rancher service ls`|List services in a stack|
|`rancher service create`|Create a new service in a stack|
|`rancher service delete <SERVICE_ID>`|Delete a service|

## Rancher Web UI

Rancher also provides a web-based user interface for managing and monitoring containers. The UI offers a graphical way to perform various actions, including creating clusters, adding nodes, managing projects, deploying stacks, and monitoring container health.

When using the Rancher web UI, you can navigate through the different sections to perform the desired actions. The UI provides a comprehensive view of your container infrastructure and allows you to interact with various Rancher resources.

It's important to note that the Rancher CLI and web UI commands mentioned here are just a subset of the available functionality. Rancher offers many more features and capabilities for managing containers and orchestrating applications. For more detailed information and advanced usage, refer to the official Rancher documentation and user guides.

---
## Remove Installation

```
kubectl delete validatingwebhookconfiguration rancher.cattle.io
kubectl delete mutatingwebhookconfiguration rancher.cattle.io
```

