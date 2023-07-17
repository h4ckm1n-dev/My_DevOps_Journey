# Disk Usage Cleanup Playbook

This playbook is used to clean up disk usage on target hosts. It performs the following tasks:

1. Cleans up the package cache.
2. Cleans up old log files.
3. Deletes old log files.
4. Cleans up temporary directories.

## Usage

1. Ensure you have Ansible installed on your control machine.
2. Update the inventory file with the target hosts on which you want to clean up disk usage.
3. Customize the playbook parameters as needed.
4. Run the playbook using the following command:

```bash

ansible-playbook -i inventory.ini cleanup-disk-usage.yml

```

Replace `inventory.ini` with your inventory file name.

## Playbook Variables

- `hosts`: Defines the target hosts where disk usage cleanup will be performed. Modify the `all` value to match the desired host group or specific hosts.

## Tasks

### Clean up package cache

This task uses the `package_cleanup` module to clean up the package cache on the target hosts. It sets the `cleanup_mode` parameter to `all` to remove all cached packages.

### Clean up old log files

This task utilizes the `find` module to search for old log files in the `/var/log` directory. It looks for files matching the `*.log` pattern that are older than 7 days. The result of the log file cleanup is registered in the `log_cleanup_result` variable.

### Delete old log files

This task uses the `file` module to delete the old log files found in the previous task. It iterates over the `log_cleanup_result.files` list and deletes each file.

### Clean up temporary directories

This task uses the `file` module to clean up the `/tmp` and `/var/tmp` directories. It deletes these temporary directories using the `absent` state.

```yml
---
- name: Clean Disk Usage
  hosts: all
  become: true
  tasks:
    - name: Clean up package cache
      package_cleanup:
        cleanup_mode: all

    - name: Clean up old log files
      find:
        paths: /var/log
        patterns: "*.log"
        age: +7
        recurse: yes
      register: log_cleanup_result

    - name: Delete old log files
      file:
        path: "{{ item.path }}"
        state: absent
      with_items: "{{ log_cleanup_result.files }}"

    - name: Clean up temporary directories
      file:
        path: "{{ item }}"
        state: absent
      with_items:
        - /tmp
        - /var/tmp
```

# Firmware Update Playbook

This playbook checks for firmware updates on target hosts using the Lenovo LXCA module. It performs the following tasks:

1. Checks for firmware updates using the `lenovo.lxca.lxca_firmware` module.
2. Determines if a system reboot is needed.
3. Reboots the system if necessary.

## Usage

1. Ensure you have Ansible installed on your control machine.
2. Update the inventory file with the target hosts on which you want to check for firmware updates.
3. Customize the playbook parameters as needed.
4. Run the playbook using the following command:

```bash

ansible-playbook -i inventory.ini firmware-update.yml

```

Replace `inventory.ini` with your inventory file name.

## Playbook Variables

- `hosts`: Defines the target hosts where firmware updates will be checked. Modify the `all` value to match the desired host group or specific hosts.

## Tasks

### Check for firmware updates

This task utilizes the `lenovo.lxca.lxca_firmware` module to check for firmware updates. It sets the `state` parameter to `present` and the `update_type` parameter to `latest`. The result of the firmware update check is registered in the `firmware_update` variable.

### Check if reboot is needed

This task sets the `reboot_needed` fact based on the value of `firmware_update.reboot_needed`. This fact will indicate whether a system reboot is required.

### Reboot if needed

This task reboots the system using the `reboot` module if a system reboot is deemed necessary. The reboot is conditionally executed based on the value of `reboot_needed`.

```yml
---

- name: Xclarity firmware update
- hosts: all
  tasks:
    - name: Check for firmware updates
      lenovo.lxca.lxca_firmware:
        state: present
        update_type: latest
      register: firmware_update

    - name: Check if reboot is needed
      set_fact:
        reboot_needed: "{{ firmware_update.reboot_needed }}"
  
    - name: Reboot if needed
      reboot:
        when: reboot_needed
```

# Update RPM Packages Playbook

This playbook is used to update RPM packages on target hosts. It performs the following tasks:

1. Updates the package cache.
2. Upgrades the RPM packages.
3. Checks for package update results.

## Usage

1. Ensure you have Ansible installed on your control machine.
2. Update the inventory file with the target hosts on which you want to update the RPM packages.
3. Customize the playbook parameters as needed.
4. Run the playbook using the following command:

```bash

ansible-playbook -i inventory.ini update-rpm-packages.yml

```

Replace `inventory.ini` with your inventory file name.

## Playbook Variables

- `hosts`: Defines the target hosts where RPM packages will be updated. Modify the `all` value to match the desired host group or specific hosts.

## Tasks

### Update package cache

This task updates the package cache on the target hosts using the `dnf makecache` command.

### Update RPM packages

This task upgrades the RPM packages on the target hosts using the `dnf upgrade --assumeyes` command. The `--assumeyes` option automatically answers "yes" to all prompts.

The result of the update operation is registered in the `update_result` variable.

### Check for package updates

This task displays the contents of the `update_result` variable, which provides information about the update operation, including any updated packages.

```yml
---
- name: Update RPM packages
  hosts: all
  become: true
  tasks:
    - name: Update package cache
      command: dnf makecache
    - name: Update RPM packages
      command: dnf upgrade --assumeyes
      register: update_result
    - name: Check for package updates
      debug:
        var: update_result
```
