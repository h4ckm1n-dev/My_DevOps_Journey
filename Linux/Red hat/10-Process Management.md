# Process Management Cheat Sheet

Managing processes is an essential task for system administration. This cheat sheet provides commands for managing processes, including process listing, termination, and monitoring in Linux.

## Process Listing

COMMAND | DESCRIPTION
---|---
`ps` | List processes running in the current session
`ps -ef` | List all processes in the system
`ps aux` | List all processes with detailed information
`pstree` | Display processes in a tree structure

## Process Termination

COMMAND | DESCRIPTION
---|---
`kill <pid>` | Send a signal to a process to terminate it gracefully
`killall <process_name>` | Terminate all processes with a specific name
`pkill <pattern>` | Send a signal to processes based on a pattern match

## Process Monitoring

COMMAND | DESCRIPTION
---|---
`top` | Display real-time system and process information
`htop` | Interactive process viewer with real-time system information
`ps aux --sort=-%cpu` | List processes sorted by CPU usage
`ps aux --sort=-%mem` | List processes sorted by memory usage
`watch <command>` | Execute a command periodically and display the output

## Background Execution and Job Control

COMMAND | DESCRIPTION
---|---
`command &` | Execute a command in the background
`bg` | Place a job in the background
`fg` | Bring a background job to the foreground
`Ctrl + Z` | Suspend a foreground job
`jobs` | List all background jobs

## Process Signals

COMMAND | DESCRIPTION
---|---
`kill -l` | List all available signals
`kill -<signal> <pid>` | Send a specific signal to a process
`pkill -<signal> <pattern>` | Send a signal to processes based on a pattern match

