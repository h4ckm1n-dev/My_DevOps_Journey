# OpenSSH Cheat-Sheet

OpenSSH is an open-source suite of secure networking utilities that provides secure remote login and file transfer capabilities. It is commonly used for securely accessing and managing remote systems over untrusted networks. Here are some key aspects and usage examples of OpenSSH

## Basic SSH Connection

COMMAND | DESCRIPTION
---|---
`ssh <user>@<host>` | Connect to a remote host using SSH
`ssh -p <port> <user>@<host>` | Connect to a remote host using a specific port

## Key Management

COMMAND | DESCRIPTION
---|---
`ssh-keygen` | Generate a new SSH key pair
`ssh-copy-id <user>@<host>` | Copy your SSH public key to a remote host
`ssh-add <private_key>` | Add a private key to the SSH agent
`ssh-keyscan <host>` | Retrieve the SSH host key

## File Transfer

COMMAND | DESCRIPTION
---|---
`scp <file> <user>@<host>:<destination>` | Copy a file to a remote host using SCP
`scp <user>@<host>:<file> <destination>` | Copy a file from a remote host using SCP
`rsync <file> <user>@<host>:<destination>` | Synchronize files to a remote host using Rsync

## Tunneling and Port Forwarding

COMMAND | DESCRIPTION
---|---
`ssh -L <local_port>:<destination_host>:<destination_port> <user>@<host>` | Local port forwarding
`ssh -R <remote_port>:<destination_host>:<destination_port> <user>@<host>` | Remote port forwarding
`ssh -D <local_port> <user>@<host>` | Dynamic port forwarding (SOCKS proxy)

## Miscellaneous

COMMAND | DESCRIPTION
---|---
`ssh -v <user>@<host>` | Increase verbosity level
`ssh -T <user>@<host>` | Disable pseudo-terminal allocation
`ssh -X <user>@<host>` | Enable X11 forwarding
`ssh -C <user>@<host>` | Enable compression
`ssh -J <user1>@<jump_host> <user2>@<target_host>` | Connect to a target host through a jump host

