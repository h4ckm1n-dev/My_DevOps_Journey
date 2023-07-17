# Rear Backup Cheat-Sheet

Relax-and-Recover (ReaR) is an open-source backup and disaster recovery solution for Linux. It helps you create a complete system backup that can be easily restored in case of system failure or data loss. This cheat-sheet provides a quick reference guide for various commands and operations related to ReaR backup.

Project Homepage: [Relax-and-Recover (ReaR)](https://rear.readthedocs.io/)

## Installation and Configuration

COMMAND | DESCRIPTION
---|---
`sudo apt-get install rear` | Install ReaR on Debian/Ubuntu
`sudo yum install rear` | Install ReaR on CentOS/RHEL
`sudo dnf install rear` | Install ReaR on Fedora
`sudo zypper install rear` | Install ReaR on openSUSE
`sudo nano /etc/rear/local.conf` | Open ReaR configuration file for editing

## Creating Backups

COMMAND | DESCRIPTION
---|---
`sudo rear -v mkbackup` | Create a ReaR backup
`sudo rear -v mkbackuponly` | Create a backup without saving it to the recovery system
`sudo rear -v mkrescue` | Create a bootable rescue image with the backup

## Restoring from Backup

COMMAND | DESCRIPTION
---|---
`sudo rear recover` | Restore a system from the ReaR backup
`sudo rear recover --rebuild-initrd` | Rebuild the initial RAM disk during the restore process
`sudo rear recover --log-file <logfile>` | Specify a custom log file for the restore process

## Customization and Advanced Options

COMMAND | DESCRIPTION
---|---
`sudo rear prepare` | Prepare the system for creating a backup
`sudo rear cleanup` | Clean up temporary files and logs created during backup/restore process
`sudo rear checklayout` | Check the layout of the recovery system
`sudo rear -v validate` | Validate the ReaR configuration and environment
`sudo rear -v mkbackup --backup-url=<URL>` | Create a backup and specify a custom backup destination URL
`sudo rear -v mkbackup --exclude-path=<path>` | Create a backup and exclude specific paths from being backed up

## Troubleshooting and Debugging

COMMAND | DESCRIPTION
---|---
`sudo rear recover --dry-run` | Perform a dry run of the restore process without making any changes
`sudo rear -v recover --fsck-source` | Run a file system check on the backup source during the restore process
`sudo rear -v recover --exclude=<path>` | Exclude specific paths from being restored during the restore process

## Reporting and Monitoring

COMMAND | DESCRIPTION
---|---
`sudo rear mkreport` | Generate a report from the last backup
`sudo rear -v mkjobreport` | Generate a report for a specific ReaR job

