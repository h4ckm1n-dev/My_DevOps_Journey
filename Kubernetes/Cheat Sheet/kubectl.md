# kubectl Cheat Sheet

kubectl is the command-line tool for interacting with Kubernetes clusters. It allows you to deploy and manage applications, inspect and manage cluster resources, and perform various administrative tasks.

## Cluster Management

COMMAND | DESCRIPTION
---|---
kubectl cluster-info | Display cluster information
kubectl config use-context CONTEXT_NAME | Switch between different cluster contexts
kubectl get nodes | List all nodes in the cluster
kubectl describe node NODE_NAME | Get detailed information about a specific node

## Namespace Management

COMMAND | DESCRIPTION
---|---
kubectl get namespaces | List all namespaces
kubectl create namespace NAMESPACE_NAME | Create a new namespace
kubectl delete namespace NAMESPACE_NAME | Delete a namespace
kubectl config set-context --current --namespace=NAMESPACE_NAME | Set the default namespace for subsequent commands

## Pod Management

COMMAND | DESCRIPTION
---|---
kubectl get pods | List all pods in the current namespace
kubectl get pods -n NAMESPACE_NAME | List pods in a specific namespace
kubectl describe pod POD_NAME | Get detailed information about a specific pod
kubectl logs POD_NAME | View logs of a specific pod
kubectl exec -it POD_NAME -- COMMAND | Execute a command in a running pod
kubectl port-forward POD_NAME LOCAL_PORT:POD_PORT | Forward a local port to a pod port
kubectl delete pod POD_NAME | Delete a pod

## Deployment Management

COMMAND | DESCRIPTION
---|---
kubectl get deployments | List all deployments in the current namespace
kubectl get deployments -n NAMESPACE_NAME | List deployments in a specific namespace
kubectl describe deployment DEPLOYMENT_NAME | Get detailed information about a specific deployment
kubectl scale deployment DEPLOYMENT_NAME --replicas=REPLICA_COUNT | Scale the number of replicas for a deployment
kubectl rollout status deployment DEPLOYMENT_NAME | Check the rollout status of a deployment
kubectl rollout undo deployment DEPLOYMENT_NAME | Rollback a deployment to the previous revision

## Service Management

COMMAND | DESCRIPTION
---|---
kubectl get services | List all services in the current namespace
kubectl get services -n NAMESPACE_NAME | List services in a specific namespace
kubectl describe service SERVICE_NAME | Get detailed information about a specific service
kubectl delete service SERVICE_NAME | Delete a service
kubectl expose deployment DEPLOYMENT_NAME --type=SERVICE_TYPE --port=SERVICE_PORT | Expose a deployment as a service

## ConfigMap and Secret Management

COMMAND | DESCRIPTION
---|---
kubectl get configmaps | List all ConfigMaps in the current namespace
kubectl get configmaps -n NAMESPACE_NAME | List ConfigMaps in a specific namespace
kubectl describe configmap CONFIGMAP_NAME | Get detailed information about a specific ConfigMap
kubectl create configmap CONFIGMAP_NAME --from-file=KEY=PATH | Create a ConfigMap from a file
kubectl get secrets | List all secrets in the current namespace
kubectl get secrets -n NAMESPACE_NAME | List secrets in a specific namespace
kubectl describe secret SECRET_NAME | Get detailed information about a specific secret
kubectl create secret generic SECRET_NAME --from-literal=KEY=VALUE | Create a secret from a literal value

## Miscellaneous

COMMAND | DESCRIPTION
---|---
kubectl apply -f FILE | Apply a configuration from a file
kubectl delete -f FILE | Delete resources defined in a file
kubectl get all | List all resources (pods, services, deployments, etc.) in the current namespace
kubectl get all -n NAMESPACE_NAME | List all resources in a specific namespace
kubectl describe RESOURCE_TYPE RESOURCE_NAME | Get detailed information about a specific resource

This cheat sheet provides some essential commands for managing and working with Kubernetes clusters using kubectl. It covers cluster management, namespace management, pod management, deployment management, service management, ConfigMap and Secret management, as well as other miscellaneous operations.

Feel free to refer to this cheat sheet for quick reference and adapt it to your specific Kubernetes deployments.
