# Networking and IP Route Cheat-Sheet

Networking and IP routing are fundamental concepts in computer networks. Understanding how to manage network interfaces, configure IP addresses, and manipulate IP routes is crucial for network administration and troubleshooting. This cheat-sheet provides a quick reference guide for various networking and IP routing commands in Linux.

## Network Interface Management

COMMAND | DESCRIPTION
---|---
`ifconfig` | Display or configure network interfaces
`ip addr show` | Show IP addresses assigned to network interfaces
`ip link set <interface> up` | Enable a network interface
`ip link set <interface> down` | Disable a network interface
`ip link show` | Show information about network interfaces

## IP Address Management

COMMAND | DESCRIPTION
---|---
`ip addr add <ip_address>/<prefix_length> dev <interface>` | Assign an IP address to a network interface
`ip addr del <ip_address>/<prefix_length> dev <interface>` | Remove an IP address from a network interface
`ip route show` | Display the IP routing table
`ip route add default via <gateway_address>` | Set the default gateway
`ip route add <network>/<prefix_length> via <next_hop>` | Add a static route
`ip route del <network>/<prefix_length>` | Delete a static route

## Network Connectivity

COMMAND | DESCRIPTION
---|---
`ping <ip_address>` | Send ICMP echo requests to a destination IP address
`ping -c <count> <ip_address>` | Specify the number of ICMP echo requests to send
`traceroute <ip_address>` | Trace the route to a destination IP address
`nslookup <domain_name>` | Perform DNS lookup for a domain name
`dig <domain_name>` | DNS lookup utility for querying DNS servers
`netstat -tuln` | Display listening ports and established network connections

## Packet Capture and Analysis

COMMAND | DESCRIPTION
---|---
`tcpdump` | Capture network packets
`tcpdump -i <interface>` | Capture packets on a specific network interface
`tcpdump -n` | Display IP addresses instead of hostnames
`wireshark` | Graphical packet capture and analysis tool

## Firewall Management

COMMAND | DESCRIPTION
---|---
`iptables` | Configure firewall rules (legacy)
`ufw` | Uncomplicated Firewall - user-friendly interface for iptables
`firewalld` | Firewall management tool (used in CentOS/RHEL 7+)

## DNS Configuration

COMMAND | DESCRIPTION
---|---
`sudo nano /etc/resolv.conf` | Edit the DNS resolver configuration file
`dig @<dns_server> <domain_name>` | Perform DNS lookup using a specific DNS server
`nslookup -type=<record_type> <domain_name>` | Query a specific DNS record type

## Network Diagnostics

COMMAND | DESCRIPTION
---|---
`ip neigh show` | Display the ARP cache (neighbor table)
`ip neigh flush all` | Clear the ARP cache
`ifconfig <interface> up` | Enable a network interface
`ifconfig <interface> down` | Disable a network interface
`mtr <ip_address>` | Network diagnostic tool combining traceroute and ping

