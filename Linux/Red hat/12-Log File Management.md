# Log File Management Cheat Sheet

Log files provide valuable information for system administration, troubleshooting, and monitoring. This cheat sheet provides commands for managing log files, including viewing, filtering, and rotating log files in Linux.

## Viewing Log Files

COMMAND | DESCRIPTION
---|---
`cat <log_file>` | Display the content of a log file
`less <log_file>` | View log file interactively with pagination
`tail <log_file>` | Display the last few lines of a log file
`tail -f <log_file>` | Continuously display new lines added to a log file
`grep <pattern> <log_file>` | Search for a specific pattern in a log file
`zcat <compressed_log_file>` | Display the content of a compressed log file

## Rotating Log Files

COMMAND | DESCRIPTION
---|---
`logrotate` | Rotate and manage log files based on predefined configurations
`logrotate -f <config_file>` | Forcefully rotate log files using a specific configuration

## Log File Locations

LOG FILE | DESCRIPTION
---|---
`/var/log/messages` | System messages and general log information
`/var/log/syslog` | System log messages
`/var/log/auth.log` | Authentication logs
`/var/log/kern.log` | Kernel logs
`/var/log/boot.log` | Boot logs
`/var/log/apache2/error.log` | Apache error logs (may vary with different web servers)
`/var/log/nginx/error.log` | Nginx error logs (may vary with different web servers)
`/var/log/mysql/error.log` | MySQL/MariaDB error logs (may vary with different database servers)

## Log File Compression

COMMAND | DESCRIPTION
---|---
`gzip <log_file>` | Compress a log file using gzip compression
`gunzip <compressed_log_file>` | Decompress a log file compressed with gzip

## Log File Permissions

COMMAND | DESCRIPTION
---|---
`chown <user>:<group> <log_file>` | Change the ownership of a log file
`chmod <permissions> <log_file>` | Change the permissions of a log file

