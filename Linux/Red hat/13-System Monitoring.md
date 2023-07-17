# System Monitoring Cheat Sheet

Monitoring system resources is crucial for system administration. This cheat sheet provides commands for monitoring CPU, memory, disk usage, and network activity in Linux.

## CPU Monitoring

COMMAND | DESCRIPTION
---|---
`top` | Display real-time system and process information
`htop` | Interactive process viewer with real-time system information
`mpstat` | Display multiple processor usage statistics
`pidstat` | Monitor individual tasks and threads usage
`lscpu` | Display CPU architecture information
`nmon` | Interactive performance monitoring tool (requires installation)

## Memory Monitoring

COMMAND | DESCRIPTION
---|---
`free` | Display system memory usage
`vmstat` | Report virtual memory statistics
`pmap` | Display memory map of a process
`smem` | Report memory usage of processes (requires installation)

## Disk Usage Monitoring

COMMAND | DESCRIPTION
---|---
`df -h` | Display disk space usage of file systems
`du -h <directory>` | Show disk usage of files and directories recursively
`iotop` | Monitor I/O usage by processes (requires installation)
`iotop -a` | Monitor I/O usage by processes continuously (requires installation)

## Network Monitoring

COMMAND | DESCRIPTION
---|---
`netstat` | Display network connections and statistics
`ss` | Utility to investigate sockets (replacement for netstat)
`nethogs` | Monitor network traffic per process (requires installation)
`iftop` | Display bandwidth usage on an interface (requires installation)
`tcpdump` | Capture and analyze network packets (requires installation)

## System Performance Monitoring

COMMAND | DESCRIPTION
---|---
`sar` | Collect, report, and save system activity information
`dstat` | Versatile resource statistics tool (requires installation)
`glances` | System monitoring tool with a customizable interface (requires installation)
`atop` | Monitor system resources and process activity (requires installation)

