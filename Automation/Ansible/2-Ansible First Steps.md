## Step 1: Update Your System

If you want a quick access to an ansible environment you need to install ansible on a [[Setting up WSL on windows#Step 0: Install Windows Subsystem for Linux (WSL-Subsystem)|WSL-Subsystem]]

Before installing Ansible, it is recommended to update the system packages. You can update your Ubuntu system with the following command:
```bash
sudo apt-get update
```

## Step 2: Install Software Properties Common

Ansible is added to the Ubuntu repositories via a Personal Package Archive (PPA). However, your system needs `software-properties-common` installed to manage these PPAs. If not already installed, you can add it with the following command:
```bash
sudo apt-get install software-properties-common
```

## Step 3: Add Ansible PPA

Once the `software-properties-common` package is installed, you can add the Ansible PPA:
```bash
sudo apt-add-repository --yes --update ppa:ansible/ansible
```

## Step 4: Install Ansible

Now, you're ready to install Ansible:
```bash
sudo apt-get install ansible
```

You can confirm the installation and check the Ansible version by running:
```bash
ansible --version
```

## Step 5: Creating an Ansible Playbook

An Ansible playbook is a file that describes the tasks to be performed by Ansible. In this case, we want to install and start Apache web server on a group of web servers.

Let's create a simple Ansible playbook named `apache.yml`:
```yaml
---
- hosts: webservers
  tasks:
    - name: ensure apache is at the latest version
      apt:
        name: apache2
        state: latest

    - name: ensure apache is running
      service:
        name: apache2
        state: started
...
```

This playbook will ensure that Apache (apache2) is installed at the latest version and that the service is running.

You would replace "webservers" with the group name of your web servers as defined in your Ansible hosts file. This is typically located in `/etc/ansible/hosts`.

## Step 6: Running the Ansible Playbook

to run your first playbook you need an inventory file, either by editing `/etc/ansible/hosts` or by creating an inventory `file ìnventory.ini` in the same folder as your playbook

let create the inventory file
```bash
sudo vi inventory.ini
```

here are some exemple on how to specify each type of host
```ini
[webservers]
web1.example.com http_port=80
web2.example.com http_port=443
web3.example.com http_port=8080 ansible_user=admin ansible_password=secretpassword
web4.example.com http_port=8080 ansible_user=admin ansible_password=secretpassword

[dbservers]
db1.example.com db_port=5432
db2.example.com db_port=5432

[loadbalancers]
lb1.example.com http_port=80
lb2.example.com http_port=80

[monitoring]
monitor.example.com ansible_user=monitor_user ansible_ssh_private_key=~/.ssh/monitor_key

[backup]
backup1.example.com backup_location=/var/backups
backup2.example.com backup_location=/var/backups

[testing]
test1.example.com ansible_user=test_user ansible_ssh_private_key=~/.ssh/test_key
test2.example.com ansible_user=test_user ansible_ssh_private_key=~/.ssh/test_key
test3.example.com ansible_user=test_user ansible_ssh_private_key=~/.ssh/test_key

```

in our case the playbook will only run on the hosts `webservers` since they are the one specified in our playbook, if we want to run the playbook on `loadbalancers` we need to update the hosts field of our playbook

To execute your Ansible playbook, you can use the following command:
```bash
ansible-playbook apache.yml
```

Ansible will then connect to your web servers, gather some facts about them, and execute the tasks defined in your playbook.

## Step 7: Verifying the Installation

To verify that Apache is installed and running on the web servers, you can try to access the default Apache page by navigating to `http://your_server_ip` in your web browser. If Apache is properly installed, you should see the Apache2 Ubuntu Default Page.

## Note:

In order for this setup to work, SSH keys must be set up between the Ansible control node (your machine) and the managed nodes (web servers). Additionally, all the web servers must have the apt package manager (common in Debian-based distributions like Ubuntu).

# use a jumphost as proxy

If you prefer to use IP addresses instead of hostnames in your Ansible inventory for configuring a jump host, you can modify the inventory file accordingly. Here's an example:

Inventory File (inventory.ini):

```ini
[jump_host]
192.0.2.1 ansible_ssh_user=jumpuser ansible_ssh_private_key=~/.ssh/jumpkey.pem

[web_servers]
192.0.2.2 ansible_ssh_common_args='-o ProxyJump=jumpuser@192.0.2.1'
192.0.2.3 ansible_ssh_common_args='-o ProxyJump=jumpuser@192.0.2.1'
```

In this example, the jump host's IP address is `192.0.2.1`, and it is defined in the `[jump_host]` group. The `ansible_ssh_user` and `ansible_ssh_private_key` variables are set to specify the SSH username and private key for the jump host.

The `[web_servers]` group contains the target hosts with IP addresses `192.0.2.2` and `192.0.2.3`. The `ansible_ssh_common_args` variable is used to configure the SSH options for the target hosts, specifying the jump host using the `-o ProxyJump=jumpuser@192.0.2.1` option.

Ensure that you update the IP addresses to match your actual jump host and target hosts.

By using IP addresses, you can establish SSH connections via the jump host and manage the remote hosts in your Ansible playbooks and commands. Remember to have the necessary SSH configurations, such as keys and access, in place for the jump host and target hosts.

Note: It's generally recommended to use hostnames whenever possible, as they provide more flexibility and can accommodate changes to IP addresses. However, if using IP addresses is necessary in your specific environment, this configuration will allow you to configure a jump host with IP addresses in Ansible.