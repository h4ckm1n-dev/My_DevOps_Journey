# NFS Cheat Sheet

NFS (Network File System) is a distributed file system protocol that allows remote file access over a network. It enables sharing files and directories between systems. This cheat sheet provides commands and concepts for working with NFS.

## NFS Terminology

TERM | DESCRIPTION
---|---
NFS Server | The system exporting its directories to be shared
NFS Client | The system mounting and accessing the shared directories
Export | A directory shared by an NFS server
Mount | The process of making a shared directory accessible on an NFS client

## NFS Server Commands

COMMAND | DESCRIPTION
---|---
`exportfs -a` | Export all directories listed in `/etc/exports`
`exportfs -r` | Refresh the list of exported directories
`exportfs -u <directory>` | Unexport a specific directory
`exportfs -v` | Display the list of exported directories

## NFS Client Commands

COMMAND | DESCRIPTION
---|---
`showmount -e <server>` | Show the list of exported directories on an NFS server
`mount <server>:<export> <mount_point>` | Mount an NFS share on the client system
`umount <mount_point>` | Unmount an NFS share
`mount -t nfs <server>:<export> <mount_point>` | Mount an NFS share using the `nfs` filesystem type
`mount -a` | Mount all filesystems defined in `/etc/fstab`
`df -h` | Display disk usage, including NFS mounts

## /etc/exports Syntax

Example entry in `/etc/exports`:

```
<directory> <client>(<options>)
```

Common options used in `/etc/exports`:

OPTION | DESCRIPTION
---|---
`ro` | Read-only access
`rw` | Read-write access
`no_root_squash` | Enable root access on the client
`no_all_squash` | Disable squashing of all UIDs and GIDs
`insecure` | Allow unprivileged ports for NFS
`sync` | Perform synchronous writes

  
## Example NFS Usage

1. On the NFS client, mount the NFS share:
    
```
    mount 192.168.0.100:/shared /mnt/nfs
```


    
2. Verify the mounted NFS share:    
```
df -h
```
    

## Troubleshooting

- If you encounter permission issues, ensure that the permissions and ownership of the shared directory on the server are properly set.
- Check the firewall settings on both the server and the client to ensure that NFS traffic is allowed.