## Step 1: Create a Namespace (Optional)

If you want to deploy Grafana in a specific namespace, you can create the namespace using the following command:

shellCopy code

`kubectl create namespace grafana`

You can choose a different namespace name if desired.

## Step 2: Add Helm Repository

Helm is a package manager for Kubernetes that allows you to install and manage applications on your cluster. Grafana provides a Helm chart for easy installation. Add the official Grafana Helm repository by running the following command:

shellCopy code

`helm repo add grafana https://grafana.github.io/helm-charts`

## Step 3: Update Helm Repositories

Before installing Grafana, update your Helm repositories to ensure you have the latest charts. Run the following command:

shellCopy code

`helm repo update`

## Step 4: Install Grafana

To install Grafana on your Kubernetes cluster, execute the following Helm command:

shellCopy code

`helm install grafana grafana/grafana --namespace grafana --set persistence.enabled=true`

This command installs Grafana using the default Helm chart with persistence enabled. The `--namespace` flag specifies the namespace where Grafana will be deployed. If you skipped Step 1 and want to deploy Grafana in the default namespace, omit the `--namespace` flag.

Wait for the installation to complete. You can monitor the progress by running the following command:

shellCopy code

`kubectl get pods -n grafana`

Once the Grafana pod is in the `Running` state, it indicates that the installation is successful.

## Step 5: Access Grafana

To access Grafana's web interface, you need to expose it as a service.

1. Determine the Grafana service name by executing the following command:
    
    shellCopy code
    
    `kubectl get services -n grafana`
    
    Look for the service with the name `grafana` and note the port number.
    
2. Create a port-forward to the Grafana service using the following command:
    
    shellCopy code
    
    `kubectl port-forward service/grafana <local_port>:<grafana_port> -n grafana`
    
    Replace `<local_port>` with the port number you want to use on your local machine (e.g., 3000), and `<grafana_port>` with the port number noted in the previous step.
    
3. Open a web browser and visit `http://localhost:<local_port>`, where `<local_port>` is the port number you specified in the previous step.
    
    This should display the Grafana login page.
    
4. To obtain the default login credentials, run the following command:
    
    shellCopy code
    
    `kubectl get secret --namespace grafana grafana -o jsonpath="{.data.admin-user}" | base64 --decode`
    
    This command retrieves the Grafana admin username. Repeat the command, replacing `admin-user` with `admin-password`, to retrieve the admin password.
    
5. Log in to Grafana using the admin credentials obtained in the previous step.