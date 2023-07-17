
[Ansible](https://ansible.com/) is an open-source automation tool that allows you to manage and configure systems, deploy applications, and orchestrate complex tasks using a declarative language. It simplifies the process of automating repetitive tasks, making it a popular choice for infrastructure provisioning and configuration management.

Here are some key concepts and features related to Ansible:

#### Inventory

Ansible uses an inventory file to define the target hosts or groups of hosts that it will manage. The inventory file is typically a plain text file or a dynamic inventory script that lists the hosts along with their connection details such as IP addresses, SSH credentials, and group assignments.

The inventory file can be organized into groups, allowing you to define common configurations and target specific subsets of hosts. This helps in managing large environments and applying configurations consistently across multiple systems.

#### Playbooks

Playbooks are written in YAML format and serve as the foundation of Ansible automation. A playbook contains a set of tasks that define the desired state of the system. Each task specifies an action to be executed, such as installing packages, copying files, or running commands.

Playbooks can be used to perform various operations, including configuration management, application deployment, and infrastructure provisioning. They allow you to define the desired state of your systems and let Ansible handle the execution and convergence towards that state.

#### Modules

Ansible provides a vast collection of modules that encapsulate specific tasks and actions. Modules are the building blocks used within tasks to perform operations on the target hosts. They cover a wide range of areas, including package management, file manipulation, user management, service control, and more.

Modules are idempotent, meaning that they will only make necessary changes to bring the system to the desired state. Ansible uses modules to abstract the underlying system differences and provide a consistent interface for automation.

#### Variables and Templates

Ansible allows you to define variables that can be used to parameterize your playbooks and make them more flexible. Variables can be defined at various levels, including inventory level, playbook level, and task level. They enable you to customize configurations and reuse playbooks across different environments.

In addition to variables, Ansible supports template files. Templates use Jinja2 syntax to dynamically generate configuration files or scripts based on variables and conditions. This allows you to create dynamic and reusable configurations that adapt to the specific requirements of each target host.

#### Roles

Roles provide a way to organize and reuse Ansible code. A role is a self-contained unit that encapsulates related tasks, variables, files, and templates into a structured directory layout. Roles promote modular and reusable automation, making it easier to share and collaborate on Ansible code.

Roles can be applied to hosts or groups of hosts, allowing you to apply a specific configuration or set of tasks to a particular set of systems. They enhance code organization and make playbook maintenance and reusability more manageable.

#### Ansible Galaxy

Ansible Galaxy is a community-driven repository of Ansible roles, playbooks, and modules. It provides a platform for sharing and discovering automation content created by the Ansible community. You can search for existing roles and playbooks on Ansible Galaxy, saving time and effort in developing your automation solutions.

#### Ansible Tower (Red Hat Ansible Automation Platform)

Ansible Tower, now part of the Red Hat Ansible Automation Platform, is a web-based user interface and management system for Ansible. It provides additional features such as job scheduling, centralized logging, RBAC (Role-Based Access Control), and automation workflow management.

Ansible Tower simplifies the management of Ansible automation across teams and provides a more scalable and enterprise-ready solution for large-scale deployments.

Ansible's simplicity, agentless architecture, and powerful automation capabilities make it a popular choice for managing infrastructure and orchestrating tasks. Whether you are automating server configurations, application deployments, or complex workflows, Ansible provides a flexible and efficient automation framework.



# Ansible Cheat-Sheet

## Inventory and Configuration

COMMAND | DESCRIPTION
---|---
`ansible --version` | Display the Ansible version
`ansible all -i inventory.ini --list-hosts` | List all hosts defined in the inventory
`ansible-playbook playbook.yml` | Run a playbook
`ansible-playbook playbook.yml --tags <tag>` | Run a playbook with specific tags
`ansible-playbook playbook.yml --skip-tags <tag>` | Run a playbook and skip specific tags

## Ad-Hoc Commands

COMMAND | DESCRIPTION
---|---
`ansible all -m ping` | Execute a ping module on all hosts
`ansible <hostname> -m command -a "command"` | Execute a command on a specific host
`ansible <groupname> -m shell -a "command"` | Execute a shell command on a specific group of hosts
`ansible all -a "command"` | Execute a command on all hosts
`ansible all -m setup` | Gather facts from all hosts

## Playbook Structure

COMMAND | DESCRIPTION
---|---
`- name: Task Name` | Define a task name in a playbook
`hosts: <hostname>` | Specify the host(s) to execute tasks on
`tasks:` | Start the list of tasks
`- name: Task Name` | Define a task name
`  module: <module_name>` | Specify the Ansible module to use
`  <module_argument>: <argument_value>` | Provide arguments to the module

## Variables and Templating

COMMAND | DESCRIPTION
---|---
`vars:` | Start the variable section in a playbook
`var_name: value` | Define a variable and assign a value
`- name: Task Name` | Define a task name
`  debug:` | Print debug information
`    msg: "Variable Value: {{ var_name }}"` | Display the value of a variable

## Loops and Conditionals

COMMAND | DESCRIPTION
---|---
`with_items:` | Iterate over a list of items
`- name: Task Name` | Define a task name
`  debug:` | Print debug information
`    msg: "Item: {{ item }}"` | Display each item in a list

## Handlers

COMMAND | DESCRIPTION
---|---
`handlers:` | Define handlers in a playbook
`- name: Handler Name` | Define a handler name
`  <module_name>: <module_argument>` | Specify the module and its argument for the handler
`  listen: "<event_name>"` | Associate the handler with a specific event
`  notify: Handler Name` | Trigger the handler

## Roles

COMMAND | DESCRIPTION
---|---
`ansible-galaxy init <role_name>` | Create a new Ansible role structure
`roles/` | Default directory for storing roles
`- hosts: all` | Define the hosts to apply a role to
`  roles:` | Apply roles to hosts
`    - <role_name>` | Specify the name of the role

