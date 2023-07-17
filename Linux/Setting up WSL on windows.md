## Step 0: Install Windows Subsystem for Linux (WSL-Subsystem)

The first step is to enable WSL on your machine. WSL allows you to run a Linux environment directly on Windows, without the overhead of a traditional virtual machine or dual-boot setup.

### Step 1: Enable WSL

Open PowerShell as an Administrator and run:
```bash
wsl --set-default-version 2
```

### Step 2: list available distro

```bash
wsl --list --online
```

let chose Ubuntu

```bash
wsl --install -d Ubuntu
```

### Step 3: Set Up Ubuntu

After installation, launch Ubuntu from the Start menu. The first time you launch it, it will complete the installation and setup.

You'll be asked to create a new user and password. This will be your user for the Ubuntu system, and it doesn't have to match your Windows username.

## Note:

This will install Ubuntu on your Windows machine, and you'll be able to use the Linux command line directly from Windows. Keep in mind that this is a terminal environment — it doesn't include a graphical user interface. However, it will be sufficient for running Ansible.

WSL Subsystem