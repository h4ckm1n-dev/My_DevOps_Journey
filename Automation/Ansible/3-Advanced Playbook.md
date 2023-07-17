**1. Introduction**

Welcome to this Ansible Playbook tutorial! Before we begin, let's cover some basics:

Ansible is an open-source software provisioning, configuration management, and application-deployment tool. It allows for infrastructure as code, which means you can manage your servers, configurations, and applications from a simple text file, rather than having to manually set up each one.

A key component of Ansible is the "Playbook." Playbooks are written in the YAML format and are essentially a set of instructions (or plays) that Ansible should perform on a host or a group of hosts. These plays can include tasks like installing software, starting or stopping services, or even pulling code from a version control system.

In this tutorial, we'll take a deep dive into Ansible playbooks. We'll start from the basics and progressively introduce more complex concepts. By the end, you'll be equipped with the knowledge to write powerful and efficient Ansible playbooks.

Let's get started!

**2. Prerequisites**

Before you begin this tutorial, you should have the following:

**Software Requirements**

1. **Ansible Installed**: This tutorial assumes that you have Ansible installed on your machine. If you do not have Ansible installed yet, please follow the official Ansible installation guide to get it set up.
    
2. **Access to a Linux Environment**: Ansible was designed for Unix-like systems, so having access to a Linux-based system, whether a virtual machine or a physical server, is necessary. This could be a local installation or a remote server.
    
3. **A Text Editor**: You will need a text editor to create and edit your playbook files. This can be a simple editor like nano or vi, or more complex ones like Visual Studio Code, Atom, or Sublime.
    

**Knowledge Requirements**

1. **Basic Linux Commands**: You should be comfortable navigating through the Linux command line, as you'll need to move around directories, edit files, and execute commands.
    
2. **YAML Understanding**: Ansible Playbooks are written in YAML (Yet Another Markup Language). Understanding how YAML files are structured will be helpful.
    
3. **Basic Understanding of Ansible**: While this tutorial will start from the basics of playbooks, having a general idea about what Ansible is and what it can do will be beneficial.
    

Now that we have the prerequisites out of the way, let's start setting up our Ansible environment!

**3. Setting Up The Environment**

Before we dive into creating our Ansible playbook, it's crucial to have our environment set up.

**Ansible Installation Check**

First, we want to ensure that Ansible is correctly installed on your machine. Open your terminal and type:
```bash
ansible --version
```

This command should output some information about your Ansible installation, including the version number. If you see an error message, it means that Ansible is not installed correctly, and you should revisit the installation guide.

**Setting Up Hosts**

Ansible works by configuring client machines that are referred to as "hosts". For Ansible to interact with these hosts, we need to define them in an inventory file.

Let's create an inventory file. You can name the file whatever you want, but for this tutorial, we'll call it `hosts.ini`.

In your terminal, type:
```bash
nano hosts.ini
```

This will open the nano text editor. Inside the hosts.ini file, you'll define your hosts like this:
```ini
[webservers]
192.168.1.10
192.168.1.11

[dbservers]
192.168.1.20
```

In the example above, we defined two groups of hosts: `webservers` and `dbservers`. Each group contains one or more IP addresses. These IP addresses are the hosts that Ansible will configure.

**SSH Key Configuration**

By default, Ansible uses SSH to connect to hosts. Therefore, it's crucial to have SSH set up and configured. The most common practice is to create an SSH key pair and distribute the public key to all your hosts.

To create an SSH key pair, in your terminal type:
```bash
ssh-keygen
```

Follow the prompts, and an SSH key pair will be created. Your public key will typically be located in `~/.ssh/id_rsa.pub`. To distribute this key to your hosts, you can use the `ssh-copy-id` command:
```bash
ssh-copy-id user@host
```

In the command above, replace `user` with the username on the host machine and `host` with the IP address of the host.

Congratulations, you've set up your Ansible environment! You're now ready to create your first playbook.

**4. Basic Playbook Structure**

Now that we've set up our environment, we can start writing our first Ansible playbook. Before we do, let's understand the basic structure of a playbook.

A playbook is a YAML file. YAML stands for "YAML Ain't Markup Language". It's a human-friendly data serialization standard that's perfect for configuration files and data exchange between languages with different data types.

A basic playbook might look like this:
```yaml
---
- name: My first playbook
  hosts: webservers
  tasks:
    - name: Ensure Apache is installed
      apt:
        name: apache2
        state: present
...

```

**Let's break it down:**

1. `---`: This is how you start a YAML file. This signals the start of a document.
    
2. `- name: My first playbook`: This is the start of a "play". A playbook can contain multiple plays. The `name` is a human-readable description of the play.
    
3. `hosts: webservers`: This defines the hosts that this play will run on. It refers to the hosts we defined in our `hosts.ini` file.
    
4. `tasks:`: This begins the list of tasks. Tasks are the actions you want Ansible to execute.
    
5. `- name: Ensure Apache is installed`: This is a task. The `name` is a human-readable description of the task.
    
6. `apt:`: This is an Ansible module. Ansible modules are small programs that do some sort of task. In this case, the `apt` module is used to manage packages on Debian-based Linux distributions.
    
7. `name: apache2`: This is an argument to the `apt` module. It specifies the name of the package to manage.
    
8. `state: present`: This is another argument to the `apt` module. It specifies that the `apache2` package should be installed.
    
9. `...`: This is how you end a YAML file. This signals the end of a document.
    

Now you understand the basic structure of an Ansible playbook! In the next chapters, we'll go into more details and cover more advanced topics.

**5. Inventory File**

In our setup, we mentioned the `hosts.ini` file, also known as an inventory file. The inventory file is a crucial part of Ansible, as it defines the hosts or group of hosts on which your playbook will be run.

A basic inventory file might look like this:
```ini
[webservers]
web1.example.com
web2.example.com

[dbservers]
db1.example.com
```

Here's a breakdown of the inventory file:

- `[webservers]` and `[dbservers]`: These are groups. They allow you to organize your hosts and execute plays on specific groups.
    
- `web1.example.com`, `web2.example.com`, `db1.example.com`: These are hosts. They can be either domain names or IP addresses.
    
- You can also define variables for hosts or groups. For example:
    
```ini
[webservers]
web1.example.com http_port=80
web2.example.com http_port=443

[dbservers]
db1.example.com db_port=5432
```

In the example above, `http_port` and `db_port` are variables. We'll cover how to use them in the playbook in the "Variables" chapter.

When running the Ansible playbook, we specify the inventory file using the `-i` flag. For example:
```bash
ansible-playbook -i hosts.ini my_playbook.yml
```

That's all about the inventory file! In the next chapter, we'll explore Ansible modules, which are the building blocks of tasks.

Please confirm when you're ready for the next chapter.

**6. Modules**

Modules are the building blocks of Ansible and Playbooks. They are essentially command-line programs that get executed in sequence according to the playbook instructions.

Ansible comes with hundreds of built-in modules that perform specific tasks like installing packages, managing files, managing services, and so on. Each module accepts a set of parameters for configuration.

We've seen the `apt` module in our basic playbook example:
```yaml
tasks:
    - name: Ensure Apache is installed
      apt:
        name: apache2
        state: present
```

In this task, the `apt` module ensures the Apache package is installed.

Let's look at some more examples:

1. **Copy Module**

The copy module is used to copy files from the local machine to remote machines. Here's an example:
```yaml
tasks:
    - name: Copy a file
      copy:
        src: /local/path/to/file.txt
        dest: /remote/path/to/file.txt
```

2. **File Module**

The file module can be used to manage files and directories. Here's an example of creating a directory:
```yaml
tasks:
    - name: Create a directory
      file:
        path: /path/to/directory
        state: directory
```

3. **Service Module**

The service module is used to manage services. For example, to ensure a service is started:
```yaml
tasks:
    - name: Ensure Apache is running
      service:
        name: apache2
        state: started
```

In the examples above, the module names are `copy`, `file`, and `service`. Each module takes different parameters.

Remember, Ansible has hundreds of modules, so you have a wide range of tasks you can perform. You can find more modules and their documentation in the official Ansible docs.
  
7. Variables**

Variables in Ansible are very flexible and powerful. They can be used to customize the behavior of your playbooks and tasks. Variables can be defined in a variety of places, including playbooks, inventory files, and variable files.

**Defining Variables in Playbooks**

Variables can be defined directly in the playbook using the `vars` keyword. Here's an example:
```yaml
- name: Install and start Apache
  hosts: webservers
  vars:
    http_port: 80
    max_clients: 200
  tasks:
    - name: Ensure Apache is installed
      apt:
        name: apache2
        state: present
    - name: Ensure Apache is running
      service:
        name: apache2
        state: started
```

In this playbook, `http_port` and `max_clients` are variables. These variables could be used in tasks if needed.

**Defining Variables in Inventory Files**

You've already seen an example of this in the Inventory File chapter. Here's a refresher:
```ini
[webservers]
web1.example.com http_port=80
web2.example.com http_port=443

[dbservers]
db1.example.com db_port=5432
```

In this inventory file, `http_port` and `db_port` are variables.

**Defining Variables in Variable Files**

For complex playbooks, it's often easier to manage variables in separate files. You can then include these files in your playbooks using the `vars_files` keyword:
```yaml
- name: Install and start Apache
  hosts: webservers
  vars_files:
    - vars/apache_vars.yml
  tasks:
    - name: Ensure Apache is installed
      apt:
        name: apache2
        state: present
    - name: Ensure Apache is running
      service:
        name: apache2
        state: started
```

In this playbook, `apache_vars.yml` is a file that contains variables.

**Using Variables**

Once you've defined a variable, you can use it in tasks like this:
```yaml
tasks:
  - name: Ensure Apache is installed
    apt:
      name: apache2
      state: present
```

In this task, `{{ filename }}` is a variable. Ansible will replace it with the value of the `filename` variable when executing the task.

That's it for variables! In the next chapter, we'll look at how to define and order tasks in a playbook.

8. Tasks and Handlers**

Tasks are the heart of an Ansible playbook. They represent the actions you want to perform on your hosts. Handlers are a special kind of task that only run when notified by another task.

**Tasks**

We've seen examples of tasks in previous chapters, but here's a refresher:
```yaml
tasks:
  - name: Ensure Apache is installed
    apt:
      name: apache2
      state: present
```

In this example, we have a single task that ensures Apache is installed. You can add as many tasks as you need in your playbook, and they will be executed in the order they are listed.

**Handlers**

Handlers are tasks that only run when notified by another task. They are typically used to restart services when a configuration file changes. Here's an example:
```yaml
tasks:
  - name: Ensure Apache is installed
    apt:
      name: apache2
      state: present
    notify: Restart Apache

  - name: Ensure Apache config file is correct
    copy:
      src: /local/path/to/apache2.conf
      dest: /etc/apache2/apache2.conf
    notify: Restart Apache

handlers:
  - name: Restart Apache
    service:
      name: apache2
      state: restarted
```

In this playbook, the "Restart Apache" handler will only run if either the "Ensure Apache is installed" task or the "Ensure Apache config file is correct" task notifies it. This is achieved using the `notify` keyword.

This mechanism ensures that services are only restarted when necessary, not every time the playbook runs.

Remember, tasks and handlers are executed in the order they are defined, so make sure you order them correctly!

In the next chapter, we'll talk about using conditionals in your tasks to control their execution.

**9. Conditionals**

In Ansible, conditionals provide the ability to execute a task or skip it based on certain conditions. The most common use of conditionals is the `when` clause.

**Using `when` Clause**

The `when` clause allows a task to be executed only when a certain condition is met. This condition can be the value of a variable, the result of a previous task, or a system fact. Here's an example:
```yaml
- name: Install Apache
  hosts: webservers
  tasks:
    - name: Install Apache on Ubuntu
      apt:
        name: apache2
        state: present
      when: ansible_os_family == "Debian"

    - name: Install Apache on CentOS
      yum:
        name: httpd
        state: present
      when: ansible_os_family == "RedHat"
```

In this playbook, the `ansible_os_family` variable is a system fact that represents the type of the operating system. The `when` clause checks this variable and runs the correct task depending on the operating system.

**Using `failed_when` and `changed_when`**

You can also define custom failure or change conditions for a task using the `failed_when` and `changed_when` clauses. Here's an example:
```yaml
- name: Check disk space
  shell: df -h / | tail -1 | awk '{print $5}' | cut -d'%' -f1
  register: disk_space
  failed_when: disk_space.stdout|int > 90
```

In this task, the `df -h /` command is used to check the disk space. The `register` keyword is used to save the output of the command in a variable called `disk_space`. The `failed_when` clause checks the value of `disk_space.stdout` and fails the task if the disk space usage is above 90%.

That's a quick overview of conditionals in Ansible. In the next chapter, we'll talk about loops, which allow you to repeat tasks multiple times.

**10. Loops**

Loops in Ansible allow you to perform a task multiple times. This is useful when you want to perform the same action on a list of items.

The most common use of loops in Ansible is with the `loop` keyword. Here's an example:
```yaml
- name: Install packages
  hosts: webservers
  vars:
    packages:
      - apache2
      - mysql-server
      - php
  tasks:
    - name: Ensure packages are installed
      apt:
        name: "{{ item }}"
        state: present
      loop: "{{ packages }}"
```

In this playbook, the `packages` variable is a list of packages to be installed. The `loop` keyword is used to iterate over this list. The `item` variable represents the current item in the loop.

**Using `dict2items` Filter**

If you want to loop over a dictionary, you can use the `dict2items` filter. Here's an example:
```bash
- name: Configure users
  hosts: webservers
  vars:
    users:
      alice:
        password: secret1
        shell: /bin/bash
      bob:
        password: secret2
        shell: /bin/zsh
  tasks:
    - name: Ensure users are present
      user:
        name: "{{ item.key }}"
        password: "{{ item.value.password }}"
        shell: "{{ item.value.shell }}"
      loop: "{{ users | dict2items }}"
```

In this playbook, the `users` variable is a dictionary. The `dict2items` filter is used to convert this dictionary into a list of items that can be looped over.

That's all about loops in Ansible! In the next chapter, we'll discuss how to manage errors and debug your playbooks.

11. Error Handling and Debugging**

When working with complex playbooks, you might encounter errors or unexpected behavior. Ansible provides several ways to handle errors and debug your playbooks.

**Error Handling**

Ansible tasks fail by default when a command returns a non-zero exit status. But you can control this behavior using the `ignore_errors` keyword:
```bash
- name: Run a command that may fail
  command: /usr/bin/somecommand
  ignore_errors: true
```

In this task, Ansible will ignore any errors from the `somecommand` command and continue executing the playbook.

Another useful keyword is `failed_when`, which allows you to define custom failure conditions:
```yaml
- name: Check disk space
  shell: df -h / | tail -1 | awk '{print $5}' | cut -d'%' -f1
  register: disk_space
  failed_when: disk_space.stdout|int > 90
```

In this task, Ansible will fail the task if the disk space usage is above 90%.

**Debugging**

The `debug` module is a helpful tool for debugging your playbooks. It allows you to print messages and variable values:
```yaml
- name: Print a variable
  debug:
    msg: "The value of the foo variable is {{ foo }}"
```

In this task, the `debug` module prints the value of the `foo` variable.

You can also use the `-vvv` flag when running `ansible-playbook` to get verbose output, which can be helpful for debugging:
```bash
ansible-playbook -i hosts.ini my_playbook.yml -vvv
```

That's a brief overview of error handling and debugging in Ansible. In the next chapter, we'll talk about how to organize your playbooks and roles for better maintainability and reuse.

**12. Organizing Playbooks and Roles**

As your Ansible projects grow in size and complexity, it's important to organize your playbooks and roles in a way that makes them easy to understand, maintain, and reuse.

**Playbook Organization**

One common approach to organizing playbooks is to have one playbook per role. For example, you might have a playbook for setting up web servers, another for database servers, and another for load balancers. You can then use these playbooks together to set up your entire infrastructure.

Here's an example directory structure for this approach:
```css
.
├── ansible.cfg
├── hosts.ini
├── web.yml
├── db.yml
└── lb.yml

```

In this structure, `web.yml`, `db.yml`, and `lb.yml` are playbooks for setting up web, database, and load balancer servers, respectively.

**Roles**

Roles are a way to group related tasks together into reusable units. For example, you might have a role for setting up Apache, another for setting up MySQL, and another for setting up PHP.

Roles are stored in a directory structure with a specific layout. Here's an example:
```css
.
└── roles
    └── apache
        ├── tasks
        │   └── main.yml
        ├── handlers
        │   └── main.yml
        ├── templates
        │   └── apache2.conf.j2
        ├── files
        │   └── index.html
        ├── vars
        │   └── main.yml
        └── defaults
            └── main.yml
```

In this structure, `tasks/main.yml` contains the tasks for the role, `handlers/main.yml` contains the handlers, `templates/` contains Jinja2 template files, `files/` contains static files, `vars/main.yml` contains role-specific variables, and `defaults/main.yml` contains default variables.

Roles can be used in playbooks using the `roles` keyword:
```yaml
- name: Setup a web server
  hosts: webservers
  roles:
    - apache
    - mysql
    - php
```

In this playbook, the `apache`, `mysql`, and `php` roles are applied to the `webservers` group.

This concludes our chapter on organizing playbooks and roles. In the final chapter, we'll discuss testing and continuous integration for your Ansible projects.

**13. Testing and Continuous Integration**

As with any codebase, testing is an essential part of the development process in Ansible. It ensures that your playbooks and roles work as expected, and it prevents regressions when you make changes.

**Testing Locally**

You can test your playbooks and roles locally using tools like Vagrant or Docker. You can create a local environment that mimics your production environment, and run your playbooks against this environment.

For example, to test a playbook with Vagrant, you can create a `Vagrantfile` that sets up a VM similar to your production servers, then run `ansible-playbook` against this VM:
```bash
vagrant up
ansible-playbook -i hosts.ini playbook.yml
```

**Automated Testing**

For automated testing, you can use tools like Molecule or Ansible Test Kitchen. These tools allow you to define test scenarios, run your playbooks against these scenarios, and verify the results.

For example, with Molecule, you can create a scenario like this:
```bash
molecule init scenario -r my_role -d docker
```

This command creates a new test scenario for the `my_role` role using Docker as the driver. You can then run the tests with this command:
```bash
molecule test
```

**Continuous Integration**

Continuous Integration (CI) takes automated testing a step further by running your tests automatically whenever you make changes to your code.

You can use a CI/CD service like Jenkins, Travis CI, or GitHub Actions to automatically run your tests every time you push to your Git repository. This ensures that your playbooks and roles are always in a deployable state.

In this chapter, we have only touched on the surface of testing and CI/CD with Ansible. These are vast topics and there are many resources available to learn more about them.

With that, we've covered all the basics you need to get started with Ansible! It's a powerful tool and there's a lot to learn, but hopefully this guide has given you a solid foundation to build on.