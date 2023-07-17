# Vagrant Cheat-Sheet

Vagrant is an open-source tool for building and managing virtual machine environments. It provides an easy and consistent workflow for creating and configuring virtual machines.

Project Homepage: [Vagrant by HashiCorp](https://www.vagrantup.com/)
Documentation: [Vagrant Documentation](https://www.vagrantup.com/docs)

## General Management
COMMAND | DESCRIPTION
---|---
`vagrant status` | Outputs the status of the Vagrant machine
`vagrant global-status` | Outputs the status of all Vagrant machines
`vagrant global-status --prune` | Same as above, but prunes invalid entries

## Managing VMs
COMMAND | DESCRIPTION
---|---
`vagrant init` | Initialize Vagrant with a Vagrantfile and ./.vagrant directory, using no specified base image. Before you can do vagrant up, you'll need to specify a base image in the Vagrantfile.
`vagrant up` | Starts the Vagrant environment (also provisions only on the FIRST vagrant up)
`vagrant halt` | Stops the Vagrant machine
`vagrant suspend` | Suspends a virtual machine (remembers state)
`vagrant resume` | Resumes a suspended machine (vagrant up works just fine for this as well)
`vagrant ssh` | Connects to the machine via SSH
`vagrant ssh <BOXNAME>` | If you give your box a name in your Vagrantfile, you can SSH into it with the box name. Works from any directory.
`vagrant destroy` | Stops and deletes all traces of the Vagrant machine
`vagrant destroy -f` | Same as above, without confirmation

## Provisioning VMs
COMMAND | DESCRIPTION
---|---
`vagrant provision` | Forces reprovisioning of the Vagrant machine
`vagrant provision --debug` | Use the debug flag to increase the verbosity of the output
`vagrant up --provision | tee provision.log` | Runs `vagrant up`, forces provisioning, and logs all output to a file

## Manage Boxes
COMMAND | DESCRIPTION
---|---
`vagrant box list` | See a list of all installed boxes on your computer
`vagrant box add <BOXNAME> <BOXURL>` | Download a box image to your computer
`vagrant box outdated` | Check for updates for installed boxes
`vagrant box update` | Update an installed box to the latest version
`vagrant box remove <BOXNAME>` | Deletes a box from the machine
`vagrant package` | Packages a running VirtualBox environment into a reusable box
