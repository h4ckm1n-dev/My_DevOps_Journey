# SSHFS Cheat Sheet

SSHFS allows you to mount a remote filesystem over SSH, enabling you to access and interact with files on a remote server as if they were on your local machine. This cheat sheet provides commands and options for effective usage of SSHFS.

## Basic Usage

COMMAND | DESCRIPTION
---|---
`sshfs <user>@<host>:<remote_path> <local_mount_point>` | Mount a remote filesystem on a local directory
`fusermount -u <local_mount_point>` | Unmount a previously mounted SSHFS filesystem

## SSHFS Options

COMMAND | DESCRIPTION
---|---
`-p <port>` | Connect to the remote host using a specific SSH port
`-C` | Enable compression during data transfer
`-o <option>` | Specify additional SSH options (e.g., `-o UserKnownHostsFile=/path/to/known_hosts`)
`-o <option>=<value>` | Set SSH options with values (e.g., `-o PasswordAuthentication=no`)
`-o reconnect` | Automatically reconnect if the connection is lost
`-o reconnect_timeout=<timeout>` | Set the timeout for reconnect attempts
`-o workaround=<workaround>` | Apply a specific workaround for SSH-related issues

## Mounting Options

COMMAND | DESCRIPTION
---|---
`-o allow_other` | Allow other users to access the mounted filesystem
`-o uid=<uid>` | Set the user ID for the mounted filesystem
`-o gid=<gid>` | Set the group ID for the mounted filesystem
`-o umask=<umask>` | Set the umask for the mounted filesystem

## SSH Authentication Options

COMMAND | DESCRIPTION
---|---
`-o IdentityFile=<private_key_file>` | Specify the private key file for SSH authentication
`-o PasswordAuthentication=no` | Disable password authentication (use key-based authentication)
`-o StrictHostKeyChecking=no` | Disable strict host key checking (not recommended for security reasons)

## Example Usages

COMMAND | DESCRIPTION
---|---
`sshfs user@example.com:/remote/folder /local/mountpoint` | Mount a remote folder on a local mount point
`sshfs -p 2222 user@example.com:/remote/folder /local/mountpoint` | Mount a remote folder using a specific SSH port
`sshfs -o IdentityFile=/path/to/private_key user@example.com:/remote/folder /local/mountpoint` | Mount a remote folder using a specific private key

