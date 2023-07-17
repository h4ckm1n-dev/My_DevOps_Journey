# Mount and fstab Cheat Sheet

## Mount Command

COMMAND | DESCRIPTION
---|---
`mount <device> <mount_point>` | Mount a filesystem from a device to a mount point
`mount -t <filesystem_type> <device> <mount_point>` | Mount a specific filesystem type
`mount -o <options> <device> <mount_point>` | Mount with specific options
`mount -a` | Mount all filesystems defined in /etc/fstab

## Common Options for Mount Command

OPTION | DESCRIPTION
---|---
`-o ro` | Mount the filesystem as read-only
`-o rw` | Mount the filesystem as read-write
`-o remount` | Remount an already mounted filesystem
`-o loop` | Mount a file as a block device
`-o user` | Allow a regular user to mount the filesystem
`-o noexec` | Prevent execution of binaries on the filesystem
`-o nosuid` | Disable setuid and setgid permissions

## fstab File

`/etc/fstab` is a configuration file that contains information about filesystems and their mount points. It is used by the `mount -a` command to mount filesystems at boot time.

Example fstab Entry:
```
<device> <mount_point> <filesystem_type> <mount_options> <dump_freq> <fsck_order>
```

Common Fields in fstab:
```
FIELD | DESCRIPTION
---|---
`<device>` | The device or partition to be mounted (e.g., /dev/sdb1, UUID)
`<mount_point>` | The directory where the filesystem will be mounted
`<filesystem_type>` | The type of the filesystem (e.g., ext4, nfs, cifs)
`<mount_options>` | Options to be used during mounting (comma-separated)
`<dump_freq>` | Used by the dump command to determine if and when the filesystem should be backed up
`<fsck_order>` | Used by the fsck command to determine the order of filesystem checks
```

## Example fstab Entries

Example Entry for an Ext4 Filesystem:
```
/dev/sdb1 /mnt/data ext4 defaults 0 2
```


Example Entry for an NFS Filesystem:
```
server:/shared /mnt/nfs nfs defaults 0 0
```


Example Entry for a Samba (CIFS) Share:
```
//server/share /mnt/smb cifs credentials=/root/.smbcredentials,uid=1000,gid=1000 0 0
```


## Useful Commands

COMMAND | DESCRIPTION
---|---
`cat /etc/fstab` | Display the contents of the fstab file
`mount -a` | Mount all filesystems defined in the fstab file
`umount <mount_point>` | Unmount a mounted filesystem

