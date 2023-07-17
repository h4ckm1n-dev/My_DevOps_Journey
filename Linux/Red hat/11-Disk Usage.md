# Disk Usage Cheat Sheet

Monitoring and managing disk usage is essential for system administration. This cheat sheet provides commands to check disk space usage, identify large files and directories, and free up disk space in Linux.

## Checking Disk Space Usage

COMMAND | DESCRIPTION
---|---
`df -h` | Display disk space usage of file systems
`df -i` | Show inode usage of file systems
`du -sh <directory>` | Display disk usage summary of a directory
`du -h <directory>` | Show disk usage of files and directories recursively

## Identifying Large Files and Directories

COMMAND | DESCRIPTION
---|---
`find <directory> -type f -size +<size> -exec ls -lh {} \;` | Find files larger than a specific size
`find <directory> -type d -size +<size> -exec ls -lh {} \;` | Find directories larger than a specific size
`du -ah <directory> | sort -rh | head -n <num>` | Show largest files and directories in descending order

## Freeing Up Disk Space

COMMAND | DESCRIPTION
---|---
`rm <file>` | Remove a file (permanently delete)
`rm -r <directory>` | Remove a directory and its contents
`rm -rf <directory>` | Forcefully remove a directory and its contents
`apt-get clean` | Clear package cache on Debian-based systems
`yum clean all` | Clear package cache on Red Hat-based systems
`journalctl --vacuum-size=<size>` | Limit the size of systemd journal logs

## Disk Usage Analysis

COMMAND | DESCRIPTION
---|---
`ncdu <directory>` | Interactive disk usage analyzer with a text-based interface
`baobab` | Graphical disk usage analyzer (GUI)

