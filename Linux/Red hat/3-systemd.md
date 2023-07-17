# Systemd Cheat Sheet

Systemd is the default init system and service manager in many Linux distributions, including Red Hat-based systems. It manages the boot process, system services, and provides a variety of management and monitoring capabilities.

## Service Management

COMMAND | DESCRIPTION
---|---
`systemctl start <service>` | Start a service
`systemctl stop <service>` | Stop a service
`systemctl restart <service>` | Restart a service
`systemctl reload <service>` | Reload the configuration of a service
`systemctl enable <service>` | Enable a service to start on boot
`systemctl disable <service>` | Disable a service from starting on boot
`systemctl status <service>` | Check the status of a service

## Unit Management

COMMAND | DESCRIPTION
---|---
`systemctl list-units` | List all active units
`systemctl list-unit-files` | List all available units
`systemctl enable <unit>` | Enable a unit to start on boot
`systemctl disable <unit>` | Disable a unit from starting on boot
`systemctl is-active <unit>` | Check if a unit is active
`systemctl is-enabled <unit>` | Check if a unit is enabled
`systemctl show <unit>` | Show details of a unit

## Logging and Journal

COMMAND | DESCRIPTION
---|---
`journalctl` | Query and display system logs
`journalctl -u <unit>` | Display logs for a specific unit
`journalctl --since "YYYY-MM-DD"` | Display logs since a specific date
`journalctl --until "YYYY-MM-DD"` | Display logs until a specific date
`journalctl -f` | Follow and display real-time logs

## Target Management

COMMAND | DESCRIPTION
---|---
`systemctl get-default` | Get the default system target
`systemctl set-default <target>` | Set the default system target
`systemctl isolate <target>` | Change to a specific target immediately

## System Control

COMMAND | DESCRIPTION
---|---
`systemctl poweroff` | Shut down the system
`systemctl reboot` | Reboot the system
`systemctl suspend` | Suspend the system
`systemctl hibernate` | Hibernate the system

