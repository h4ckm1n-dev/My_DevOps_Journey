# FirewallD Cheat Sheet

FirewallD is a dynamic firewall management tool that provides an interface for managing firewall rules in Red Hat-based Linux distributions. It offers an easy-to-use command-line and graphical interface for configuring network traffic filtering and network zone settings.

## Basic FirewallD Commands

COMMAND | DESCRIPTION
---|---
`firewall-cmd --state` | Check the firewall status
`firewall-cmd --get-zones` | List available firewall zones
`firewall-cmd --get-default-zone` | Display the default firewall zone
`firewall-cmd --get-active-zones` | List active zones and interfaces
`firewall-cmd --zone=<zone> --list-all` | Display detailed information about a specific zone

## Zone Management

COMMAND | DESCRIPTION
---|---
`firewall-cmd --get-default-zone` | Display the default zone
`firewall-cmd --set-default-zone=<zone>` | Set the default zone
`firewall-cmd --reload` | Reload firewall rules
`firewall-cmd --permanent --zone=<zone> --add-service=<service>` | Allow incoming traffic for a specific service in a zone
`firewall-cmd --permanent --zone=<zone> --remove-service=<service>` | Remove a service from the allowed list in a zone
`firewall-cmd --zone=<zone> --add-interface=<interface>` | Assign an interface to a zone
`firewall-cmd --zone=<zone> --remove-interface=<interface>` | Remove an interface from a zone

## Service and Port Management

COMMAND | DESCRIPTION
---|---
`firewall-cmd --permanent --zone=<zone> --add-port=<port>/tcp` | Allow incoming TCP traffic for a specific port in a zone
`firewall-cmd --permanent --zone=<zone> --add-port=<port>/udp` | Allow incoming UDP traffic for a specific port in a zone
`firewall-cmd --permanent --zone=<zone> --remove-port=<port>/tcp` | Remove a TCP port from the allowed list in a zone
`firewall-cmd --permanent --zone=<zone> --remove-port=<port>/udp` | Remove a UDP port from the allowed list in a zone

## Logging and Troubleshooting

COMMAND | DESCRIPTION
---|---
`firewall-cmd --get-log-denied` | Check if logging of denied packets is enabled
`firewall-cmd --set-log-denied=all` | Enable logging of all denied packets
`firewall-cmd --set-log-denied=off` | Disable logging of denied packets
`firewall-cmd --query-masquerade` | Check if masquerading is enabled
`firewall-cmd --add-forward-port` | Forward incoming traffic to a specific port

## Other Useful Commands

COMMAND | DESCRIPTION
---|---
`firewall-cmd --list-services` | List services allowed in the default zone
`firewall-cmd --list-ports` | List ports allowed in the default zone
`firewall-cmd --panic-on` | Activate the panic mode (block all incoming and outgoing traffic)
`firewall-cmd --panic-off` | Deactivate the panic mode
`firewall-cmd --query-panic` | Check if the panic mode is active

