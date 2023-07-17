# UFW Cheat Sheet

`ufw` (Uncomplicated Firewall) is a command-line tool for managing firewall rules on Ubuntu and Debian-based systems. It provides a simplified interface for configuring firewall settings. This cheat sheet provides an overview of commonly used `ufw` commands and options.

## Basic Usage

COMMAND | DESCRIPTION
---|---
`ufw enable` | Enable the firewall (turn on)
`ufw disable` | Disable the firewall (turn off)
`ufw status` | Show the current status of the firewall and the rules
`ufw allow <port>` | Allow incoming traffic on a specific port
`ufw allow <service>` | Allow incoming traffic for a specific service (e.g., ssh, http)
`ufw deny <port>` | Deny incoming traffic on a specific port
`ufw deny <service>` | Deny incoming traffic for a specific service
`ufw delete <rule_number>` | Delete a specific rule by its rule number
`ufw reload` | Reload the firewall rules (apply changes)
`ufw reset` | Reset the firewall to default settings (disable and delete all rules)

## Advanced Usage

COMMAND | DESCRIPTION
---|---
`ufw status verbose` | Show detailed status including numbered rules
`ufw logging on` | Enable firewall logging
`ufw logging off` | Disable firewall logging
`ufw limit <port>` | Limit incoming traffic rate on a specific port
`ufw delete allow <port>` | Delete a specific allow rule for a port
`ufw delete allow <service>` | Delete a specific allow rule for a service
`ufw delete deny <port>` | Delete a specific deny rule for a port
`ufw delete deny <service>` | Delete a specific deny rule for a service

## Common Service Names

SERVICE NAME | PORT NUMBER
---|---
ssh | 22
http | 80
https | 443
ftp | 21
smtp | 25
dns | 53
mysql | 3306
postgresql | 5432

## Examples

EXAMPLE | DESCRIPTION
---|---
`ufw allow 22` | Allow incoming SSH traffic (port 22)
`ufw allow ssh` | Allow incoming SSH traffic (using service name)
`ufw deny 80` | Deny incoming HTTP traffic (port 80)
`ufw delete 3` | Delete rule number 3 from the firewall
`ufw status numbered` | Show numbered rules with detailed status

## Enable UFW

To check if ufw is enabled, run:
```bash
sudo ufw status
```

To enable UFW on your system, run:
```bash
sudo ufw enable
```

If for some reason you need to disable UFW, you can do so with the following command:
```bash
sudo ufw disable
```

Block an IP Address

## Block an IP Address/Subnet

```bash
sudo ufw deny from 203.0.113.0/24
```


