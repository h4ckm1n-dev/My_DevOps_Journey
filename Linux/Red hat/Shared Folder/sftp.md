# SFTP Cheat Sheet

SFTP is a secure file transfer protocol that provides secure file transfer and file management capabilities over SSH. This cheat sheet provides commands and options for effective usage of SFTP.

## Basic Usage

COMMAND | DESCRIPTION
---|---
`sftp <user>@<host>` | Connect to a remote host using SFTP
`sftp -P <port> <user>@<host>` | Connect to a remote host using a specific port
`sftp <user>@<host>:<remote_path>` | Connect to a remote host and navigate to a specific directory
`quit` or `exit` | Exit the SFTP session

## File and Directory Operations

COMMAND | DESCRIPTION
---|---
`ls` or `dir` | List files and directories in the current remote directory
`cd <directory>` | Change the remote directory
`pwd` | Print the current remote directory
`mkdir <directory>` | Create a new remote directory
`rmdir <directory>` | Remove a remote directory
`rm <file>` | Remove a remote file
`get <file>` | Download a remote file to the local system
`put <file>` | Upload a local file to the remote system
`rename <old_name> <new_name>` | Rename a remote file or directory

## Navigation and Permissions

COMMAND | DESCRIPTION
---|---
`lpwd` | Print the current local directory
`lcd <directory>` | Change the local directory
`chmod <permissions> <file>` | Change the permissions of a remote file
`chown <owner> <file>` | Change the owner of a remote file
`chgrp <group> <file>` | Change the group of a remote file

## Transfer Options

COMMAND | DESCRIPTION
---|---
`get -r <directory>` | Recursively download a remote directory and its contents
`put -r <directory>` | Recursively upload a local directory and its contents
`mget <pattern>` | Download multiple remote files matching a pattern
`mput <pattern>` | Upload multiple local files matching a pattern

## Other Commands

COMMAND | DESCRIPTION
---|---
`! <command>` | Execute a local shell command
`help` | Display the list of available SFTP commands
`!` or `?` | Repeat the previous command

