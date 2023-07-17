
This tutorial will guide you through the process of creating a simple Ansible playbook. We will create a playbook to install and start the Apache web server on a group of web servers.

## Step 1: Create an Inventory File (`inventory.ini`)

The inventory file is where you list the hosts (servers) that Ansible will manage. Create a file named `inventory.ini` with the following content:

```ini
[webservers]
192.168.1.10 ansible_user=user1
192.168.1.11 ansible_user=user2
192.168.1.12 ansible_user=user3
```

In this example, we have added the `ansible_user` parameter to specify the SSH user for each host. You can replace `user1`, `user2`, and `user3` with the appropriate usernames for your hosts.

By specifying the `ansible_user` parameter, Ansible will use the specified user to connect to the respective host during playbook execution or when running Ansible commands.

For example, if you have a task in your playbook that requires elevated privileges and you want to use a different user with sudo access, you can include the `become` parameter to switch to the privileged user. Here's an example task:

```yml
- name: Example task with become
  become: true
  shell: echo "This task is run with elevated privileges"

```

In this case, Ansible will use the SSH user specified in the inventory file (`ansible_user`) to connect to the host, and then the `become` parameter will allow the task to be executed with elevated privileges using the appropriate user's sudo access.

Remember to adjust the inventory file and task definitions based on your specific requirements and host configurations.

## Step 2: Create a Variables File (`vars.yml`)

In this step, we will create a file named `vars.yml` to store variables that will be used in the playbook. However, when it comes to storing sensitive information like passwords, it is recommended to use Ansible Vault for encryption.

1. Create a new vault-encrypted file named `vars.yml` using the `ansible-vault` command:
```bash
ansible-vault create vars.yml
```
`ansible-vault create vars.yml`

2. Enter and confirm a password for the vault. Make sure to remember this password as it will be required to access and edit the vault-encrypted file in the future.
    
3. Add the variables and their corresponding values to the `vars.yml` file:
```yml
---
apache_package_name: apache2
website_directory: /var/www/html
db_password: sensitivepassword123
```

In this example, `db_password` is a sensitive variable that holds a password. The vault-encrypted file ensures that the password is securely stored and can only be accessed with the correct password.

4. Save and close the `vars.yml` file.

Now, whenever you need to use the variables from the `vars.yml` file in your playbook, you can decrypt and access them by providing the vault password.

For example, in your playbook (`main.yml`), you can reference the variables like this:
```yml
---
- hosts: webservers
  vars_files:
    - vars.yml
  tasks:
    - name: Ensure Apache is at the latest version
      apt:
        name: "{{ apache_package_name }}"
        state: latest

    - name: Create a directory for website files
      file:
        path: "{{ website_directory }}"
        state: directory

    - name: Ensure Apache service is running
      service:
        name: "{{ apache_package_name }}"
        state: started

    - name: Example task using the vault-encrypted password
      shell: echo "{{ db_password }}"

```

Remember to adjust the variables, tasks, and filenames based on your specific requirements and use cases.

Please note that when running a playbook that uses a vault-encrypted file, you need to provide the vault password using the `--ask-vault-pass` option or by storing the password in a file and using the `--vault-password-file` option.

By using Ansible Vault, you can securely store sensitive information like passwords and ensure that they are protected when working with your Ansible playbooks.
## Step 3: Create a Playbook (`main.yml`)

In this step, we will create the main playbook file named `main.yml` and demonstrate how to reference variables from the vault-encrypted `vars.yml` file.

1. Create a new playbook file named `main.yml`:
```yml
---
- hosts: webservers
  vars_files:
    - vars.yml
  tasks:
    - name: Ensure Apache is at the latest version
      apt:
        name: "{{ apache_package_name }}"
        state: latest

    - name: Create a directory for website files
      file:
        path: "{{ website_directory }}"
        state: directory

    - name: Ensure Apache service is running
      service:
        name: "{{ apache_package_name }}"
        state: started

```

In this example, the playbook defines three tasks: ensuring Apache is at the latest version, creating a directory for website files, and ensuring the Apache service is running.

2. Save and close the `main.yml` file.

Now, when executing the playbook, you will need to provide the vault password to access and decrypt the `vars.yml` file.

## Step 4: Run the Playbook

Now, when executing the playbook, you will need to provide the vault password to access and decrypt the `vars.yml` file.

For example, to run the playbook with the vault-encrypted variables, use the following command:

```bash
ansible-playbook -i inventory.ini main.yml
```

Ansible will prompt you to enter the vault password interactively, and upon successful decryption, it will execute the tasks defined in the playbook using the variables from the `vars.yml` file.

Make sure to adjust the playbook tasks, filenames, and other details based on your specific requirements and use cases.

Remember that the vault-encrypted file should always be handled securely, and the vault password should be protected and shared only with authorized individuals who need access to the sensitive information.

## Step 5: Further Learning

This is a basic introduction to Ansible playbooks. Ansible is a powerful tool with many features, including roles, variables, and handlers. For more advanced usage, check out the [official Ansible documentation](https://docs.ansible.com/ansible/latest/user_guide/playbooks_intro.html).

Remember to replace the placeholders with your actual server details and tasks. Happy automating!