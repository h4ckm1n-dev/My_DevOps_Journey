# Nmap Cheat-Sheet

Nmap (Network Mapper) is a powerful open-source network scanning tool used for network exploration and security auditing. It provides a wide range of features for scanning and analyzing network hosts, services, and vulnerabilities. Here are some key features and usage examples of Nmap

## Basic Scanning

COMMAND | DESCRIPTION
---|---
`nmap <target>` | Perform a basic scan on the target
`nmap -p <port> <target>` | Scan a specific port on the target
`nmap -p- <target>` | Scan all ports on the target
`nmap -F <target>` | Fast scan, only common ports
`nmap -sP <target>` | Ping scan, discover hosts on the network
`nmap -A <target>` | Aggressive scan, enable OS detection and version detection

## Advanced Scanning

COMMAND | DESCRIPTION
---|---
`nmap -sS <target>` | TCP SYN scan
`nmap -sU <target>` | UDP scan
`nmap -sT <target>` | TCP connect scan
`nmap -sV <target>` | Version detection
`nmap -O <target>` | OS detection
`nmap -p- --min-rate=5000 <target>` | Scan all ports with a minimum rate of 5000 packets per second

## Output Options

COMMAND | DESCRIPTION
---|---
`nmap -oN output.txt <target>` | Save results in normal text format
`nmap -oX output.xml <target>` | Save results in XML format
`nmap -oG output.grep <target>` | Save results in grepable format
`nmap -oA output <target>` | Save results in all formats (normal, XML, grepable)

## Scripting Engine

COMMAND | DESCRIPTION
---|---
`nmap --script <script> <target>` | Run a specific script
`nmap --script <script1,script2> <target>` | Run multiple scripts
`nmap --script vuln <target>` | Run vulnerability scripts
`nmap --script-args <args> <target>` | Pass arguments to scripts

## Timing and Performance

COMMAND | DESCRIPTION
---|---
`nmap -T<0-5> <target>` | Set the timing template (0 = Paranoid, 5 = Insane)
`nmap --min-parallelism <value> <target>` | Set the minimum number of parallel probes
`nmap --max-parallelism <value> <target>` | Set the maximum number of parallel probes
`nmap --max-retries <value> <target>` | Set the maximum number of port scan probe retransmissions

## Firewall Evasion

COMMAND | DESCRIPTION
---|---
`nmap -f <target>` | Fragment packets to bypass filters
`nmap -D <decoy1,decoy2> <target>` | Use decoy scanning
`nmap --data-length <size> <target>` | Append random data to packets
`nmap --source-port <port> <target>` | Use a specific source port
`nmap --badsum <target>` | Send packets with bad checksums

## Miscellaneous

COMMAND | DESCRIPTION
---|---
`nmap -v <target>` | Increase verbosity level
`nmap -h` | Show the Nmap help menu
`nmap -sL` | List targets without scanning


