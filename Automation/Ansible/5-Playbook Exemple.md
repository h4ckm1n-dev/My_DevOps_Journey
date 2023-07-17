let's dissect a playbook

here is the first bloc of our playbook
```yml
- hosts: your-target-hosts
  gather_facts: yes
  tasks:
    ...
```

- `hosts: your-target-hosts` specifies the hosts or group of hosts on which the playbook tasks will be executed.
- `gather_facts: yes` instructs Ansible to collect facts about the target hosts before executing the tasks. Facts include system information, such as the operating system, IP address, and available resources.

```yml
    - name: Ensure script directory exists
      file:
        path: /usr/local/bin/log_exporter/
        state: directory
```

- This task ensures that the `/usr/local/bin/log_exporter/` directory exists on the target hosts. If the directory doesn't exist, it will be created.

```yml
    - name: Copy script files to the target hosts
      copy:
        src: "./{{ item }}"
        dest: "/usr/local/log_exporter/{{ item }}"
        mode: 0755
      with_items:
        - log_exporter.sh
        - log_exporter_retry.sh
```

- This task copies the `log_exporter.sh` and `log_exporter_retry.sh` script files from the Ansible control machine to the target hosts' `/usr/local/log_exporter/` directory. The files are given executable permissions (mode: 0755) to ensure they can be executed.

```yml
    - name: Install cron job for script log_exporter.sh (every Tuesday at 3 AM)
      become: yes
      ansible.builtin.cron:
        name: "log_exporter.sh weekly"
        user: root
        minute: "0"
        hour: "3"
        day: "*"
        weekday: "2"
        job: "/usr/local/bin/log_exporter/log_exporter.sh -scp > /dev/null 2>&1"
```

- This task sets up a cron job to run the `log_exporter.sh` script every Tuesday at 3 AM as the root user. The script is executed with the `-scp` argument, and its output is redirected to `/dev/null`.

```yml
    - name: Install cron job for script log_exporter_retry.sh (every weekday at 3 AM)
      become: yes
      ansible.builtin.cron:
        name: "log_exporter.sh weekday"
        user: root
        minute: "0"
        hour: "3"
        day: "*"
        weekday: "1-5"
        job: "/usr/local/bin/log_exporter/log_exporter_retry.sh -scp > /dev/null 2>&1"

```

- This task sets up a cron job to run the `log_exporter_retry.sh` script every weekday (Monday to Friday) at 3 AM as the root user. The script is executed with the `-scp` argument, and its output is redirected to `/dev/null`.

```yml
    - name: Copy logrotate configuration file and restart logrotate service
      become: yes
      copy:
        src: "./log_exporter_logrotate.conf"
        dest: "/etc/logrotate.d/log_exporter_logrotate.conf"
      notify: restart logrotate
```
- This task copies the `log_exporter_logrotate.conf` configuration file from the Ansible control machine to `/etc/logrotate.d/` directory on the target hosts. After copying, it triggers the `restart logrotate` handler.

```yml
  handlers:
    - name: restart logrotate
      systemd:
        name: logrotate
        state: restarted
```

- The `restart logrotate` handler restarts the `logrotate` service on the target hosts using the `systemd` module. This ensures that the logrotate service picks up the new configuration file.

Remember to adjust the playbook according to your specific requirements, including the target hosts, file paths, script names, cron schedules, and any other necessary modifications.

Here is the full playbook we just created

```yml
- hosts: your-target-hosts
  gather_facts: yes
  tasks:
    - name: Ensure script directory exists
      file:
        path: /usr/local/bin/log_exporter/
        state: directory
  
    - name: Copy script files to the target hosts
      copy:
        src: "./{{ item }}"
        dest: "/usr/local/log_exporter/{{ item }}"
        mode: 0755
      with_items:
        - log_exporter.sh
        - log_exporter_retry.sh
  
    - name: Install cron job for script log_exporter.sh (every Thuesday at 3 AM)
      become: yes
      ansible.builtin.cron:
        name: "log_exporter.sh weekly"
        user: root
        minute: "0"
        hour: "3"
        day: "*"
        weekday: "2"
        job: "/usr/local/bin/log_exporter/log_exporter.sh -scp > /dev/null 2>&1"
  
    - name: Install cron job for script log_exporter_retry.sh (every weekday at 3 AM)
      become: yes
      ansible.builtin.cron:
        name: "log_exporter.sh weekday"
        user: root
        minute: "0"
        hour: "3"
        day: "*"
        weekday: "1-5"
        job: "/usr/local/bin/log_exporter/log_exporter_retry.sh -scp > /dev/null 2>&1"
    - name: Copy logrotate configuration file and restart logrotate service
      become: yes
      copy:
        src: "./log_exporter_logrotate.conf"
        dest: "/etc/logrotate.d/log_exporter_logrotate.conf"
      notify: restart logrotate
  
  handlers:
    - name: restart logrotate
      systemd:
        name: logrotate
        state: restarted
```

Then to run the playbook, we just need to run the following command
```bash
ansible log_exporter.yaml --ask-become
```

(the playbook need log_exporter.sh and log_exporter_retry.sh from log_exporter projet to work)