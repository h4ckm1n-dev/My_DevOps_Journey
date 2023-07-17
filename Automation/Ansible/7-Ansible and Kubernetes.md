## Prerequisites

Before you begin, ensure you have the following prerequisites:

1. Ansible: Install Ansible on your control machine by following the [official Ansible installation guide](https://docs.ansible.com/ansible/latest/installation_guide/index.html).
    
2. Kubernetes Cluster: Set up a Kubernetes cluster. You can use a local cluster like Minikube or a cloud-based Kubernetes service such as Amazon EKS, Google Kubernetes Engine (GKE), or Azure Kubernetes Service (AKS).
    
3. kubectl: Install `kubectl`, the Kubernetes command-line tool, to interact with your cluster. Refer to the [official Kubernetes documentation](https://kubernetes.io/docs/tasks/tools/) for installation instructions.
    
4. Ansible Roles: Install the `kubernetes.core` and `kubernetes.cluster` roles. Run the following command:
```bash
ansible-galaxy install geerlingguy.kubernetes_core geerlingguy.kubernetes_cluster
```
  
These roles provide a set of reusable Ansible tasks and templates for managing Kubernetes resources. 

## Tutorial

Follow the steps below to use Ansible with your Kubernetes cluster:

### Step 1: Create an Ansible Inventory

1. Create an inventory file (e.g., `inventory.ini`) that defines the Kubernetes cluster nodes. For example:
```ini
[kubernetes_cluster]
master ansible_host=192.168.1.100
worker1 ansible_host=192.168.1.101
worker2 ansible_host=192.168.1.102
```

Replace the IP addresses and hostnames with the actual information for your Kubernetes cluster nodes.

### Step 2: Create an Ansible Playbook

1. Create a playbook file (e.g., `kubernetes-playbook.yml`) that defines the tasks you want to perform on the Kubernetes cluster. For example:
```yaml
 ---
- name: Install Nginx Ingress Controller
  hosts: kubernetes_cluster
  become: true
  gather_facts: false

  roles:
    - geerlingguy.kubernetes_core
    - geerlingguy.kubernetes_cluster

  vars:
    kubernetes_cluster_name: mycluster
    kubernetes_core_version: v1.21.2
    kubernetes_cluster_role: master
    kubernetes_cluster_child_node_labels: node-type=worker

```

This example playbook installs the Nginx Ingress Controller on the Kubernetes cluster using the `geerlingguy.kubernetes_core` and `geerlingguy.kubernetes_cluster` roles.

2. Customize the playbook variables (`kubernetes_cluster_name`, `kubernetes_core_version`, `kubernetes_cluster_role`, `kubernetes_cluster_child_node_labels`, etc.) according to your cluster configuration and requirements.
    

### Step 3: Run the Ansible Playbook

1. Run the playbook using the following command:

    ```bash
 ansible-playbook -i inventory.ini kubernetes-playbook.yml
```
    Replace `inventory.ini` with your inventory file name, and `kubernetes-playbook.yml` with your playbook file name.
    
    Ansible will connect to the Kubernetes cluster nodes defined in the inventory and execute the tasks specified in the playbook.
    

### Step 4: Verify the Results

1. After the playbook execution is complete, verify the desired changes on your Kubernetes cluster. For example, check if the Nginx Ingress Controller is deployed successfully by running:
```bash
 kubectl get pods -n ingress-nginx
```

This command lists the pods in the `ingress-nginx` namespace, where the Ingress Controller is typically deployed.  

Congratulations! You have successfully used Ansible to manage your Kubernetes cluster. You can continue expanding your playbook to include additional tasks such as deploying applications, managing secrets, scaling resources, and more. Ansible's powerful automation capabilities enable you to streamline and automate various operations on your Kubernetes infrastructure.

## you can install `kubectl` locally and use it in your Ansible playbook to interact with your Kubernetes cluster. Here's how you can set it up:

1. Install `kubectl` on your local machine by following the official Kubernetes documentation for your operating system: [Installing kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/).
    
2. Once `kubectl` is installed, verify that it's working correctly by running the following command in your terminal:
```bash
kubectl version --client
```

This command should display the version of `kubectl` installed on your machine.
 
3. In your Ansible playbook, use the `command` module to execute `kubectl` commands. Here's an example playbook snippet:
     ```yaml
---
- name: Example Kubernetes Playbook
  hosts: localhost
  gather_facts: false
  become: false

  tasks:
    - name: Check Kubernetes cluster info
      command: kubectl cluster-info
      register: cluster_info

    - name: Print cluster info
      debug:
        var: cluster_info.stdout_lines

```
    
    In this example, the playbook executes the `kubectl cluster-info` command and registers the output in the `cluster_info` variable. You can then use the registered variable to further process or display the results.
    
4. Run the Ansible playbook using the following command:
```bash
ansible-playbook your-playbook.yml
```
 
Replace `your-playbook.yml` with the name of your playbook file.


Ensure that the machine where you're running the playbook has connectivity to your Kubernetes cluster and the necessary permissions to execute `kubectl` commands. You may need to configure the appropriate Kubernetes context by setting the `KUBECONFIG` environment variable or using other authentication mechanisms, depending on your cluster setup.

Using `kubectl` in your Ansible playbook allows you to interact with your Kubernetes cluster, manage resources, deploy applications, retrieve information, and perform various operations as needed.