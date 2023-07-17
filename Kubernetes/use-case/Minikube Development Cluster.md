

This documentation provides step-by-step instructions for creating a development cluster using Minikube. Minikube is a tool that allows you to run a single-node Kubernetes cluster on your local machine for development and testing purposes.

## Prerequisites

Before proceeding with the cluster creation, ensure that you have the following prerequisites:

1. **Minikube**: Install Minikube by following the instructions in the [official Minikube documentation](https://minikube.sigs.k8s.io/docs/start/).
    
2. **Hypervisor**: Choose and install a hypervisor based on your operating system. Minikube supports multiple hypervisors such as VirtualBox, Hyper-V, and KVM. Refer to the Minikube documentation for instructions on setting up the appropriate hypervisor.
    
3. **kubectl**: Install `kubectl`, the Kubernetes command-line tool, to interact with your cluster. You can find installation instructions in the [official Kubernetes documentation](https://kubernetes.io/docs/tasks/tools/).
    

## Step 1: Start Minikube

To create a development cluster, follow these steps:

1. Open a terminal or command prompt.
    
2. Start Minikube by running the following command:
    
    shellCopy code
    
    `minikube start --vm-driver=<your_vm_driver>`
    
    Replace `<your_vm_driver>` with the name of the hypervisor you installed (e.g., `virtualbox`, `hyperv`, `kvm2`). This command initializes and starts a virtual machine with a single-node Kubernetes cluster.
    
3. Minikube will download the necessary ISO image and start the virtual machine. Wait for the process to complete. This may take a few minutes depending on your internet connection and system resources.
    
4. Once Minikube is up and running, verify the cluster status by executing:
    
    shellCopy code
    
    `kubectl cluster-info`
    
    This command displays information about your Kubernetes cluster, confirming that Minikube is running correctly.
    

## Step 2: Interact with the Cluster

With the development cluster created, you can now interact with it using `kubectl`.

1. To view the list of nodes in your cluster, run the following command:
    
    shellCopy code
    
    `kubectl get nodes`
    
    This displays the single node that Minikube created.
    
2. To deploy applications and manage resources on the cluster, you can use `kubectl` commands. For example, to create a simple nginx deployment, execute the following command:
    
    shellCopy code
    
    `kubectl create deployment nginx --image=nginx:latest`
    
    This creates a deployment named `nginx` using the `nginx:latest` Docker image.
    
3. To verify that the deployment is running, run the following command:
    
    shellCopy code
    
    `kubectl get deployments`
    
    You should see the `nginx` deployment listed along with its desired and current replicas.
    
4. To access the nginx deployment, expose it as a service by executing the following command:
    
    shellCopy code
    
    `kubectl expose deployment nginx --port=80 --type=NodePort`
    
    This creates a service that exposes the deployment on a randomly assigned port.
    
5. To access the nginx service, run the following command:
    
    shellCopy code
    
    `minikube service nginx`
    
    Minikube opens a browser window displaying the nginx welcome page. If it doesn't open automatically, you can copy the URL from the terminal and open it in your preferred browser.
    

## Step 3: Cleanup

Once you are finished with your development cluster, you can clean up by deleting the Minikube cluster.

1. To stop the cluster, run the following command:
    
    shellCopy code
    
    `minikube stop`
    
2. To delete the cluster, run the following command:
    
    shellCopy code
    
    `minikube delete`
    
    This deletes the Minikube virtual machine and cleans up any resources associated with the cluster.