# Metricbeat Cheat-Sheet

Metricbeat is a lightweight data shipper that collects and sends system and service metrics to various outputs, such as Elasticsearch, Logstash, or Kafka. It is part of the Elastic Stack and is designed to monitor and gather metrics from different sources in real-time.

Project Homepage: [Metricbeat by Elastic](https://www.elastic.co/beats/metricbeat)

## Installation and Configuration

COMMAND | DESCRIPTION
---|---
`sudo apt-get install metricbeat` | Install Metricbeat on Debian/Ubuntu
`sudo yum install metricbeat` | Install Metricbeat on CentOS/RHEL
`sudo dnf install metricbeat` | Install Metricbeat on Fedora
`sudo brew install metricbeat` | Install Metricbeat on macOS using Homebrew
`sudo choco install metricbeat` | Install Metricbeat on Windows using Chocolatey
`sudo nano /etc/metricbeat/metricbeat.yml` | Open Metricbeat configuration file for editing

## Modules and Metricsets

COMMAND | DESCRIPTION
---|---
`metricbeat modules enable <module>` | Enable a specific module
`metricbeat modules disable <module>` | Disable a specific module
`metricbeat modules list` | List available modules
`metricbeat modules list-enabled` | List enabled modules
`metricbeat metricsets list` | List available metricsets for a module

## Starting and Stopping Metricbeat

COMMAND | DESCRIPTION
---|---
`sudo systemctl start metricbeat` | Start Metricbeat service
`sudo systemctl stop metricbeat` | Stop Metricbeat service
`sudo systemctl restart metricbeat` | Restart Metricbeat service
`sudo systemctl enable metricbeat` | Configure Metricbeat to start on boot

## Testing Configuration and Debugging

COMMAND | DESCRIPTION
---|---
`sudo metricbeat test config` | Test the Metricbeat configuration file syntax
`sudo metricbeat test output` | Test the connection to the configured output

## Monitoring and Metrics Collection

COMMAND | DESCRIPTION
---|---
`sudo metricbeat setup` | Load the index template in Elasticsearch and setup Kibana dashboards
`sudo metricbeat -e` | Start Metricbeat in foreground and print output to the console
`sudo metricbeat export template > template.json` | Export the Elasticsearch index template

## Security and SSL/TLS

COMMAND | DESCRIPTION
---|---
`sudo metricbeat keystore create` | Create a keystore for secure storage of sensitive data
`sudo metricbeat keystore add <name>` | Add a value to the keystore
`sudo metricbeat keystore remove <name>` | Remove a value from the keystore
`sudo metricbeat keystore list` | List all values stored in the keystore

## Upgrading Metricbeat

COMMAND | DESCRIPTION
---|---
`sudo apt-get update && sudo apt-get upgrade metricbeat` | Upgrade Metricbeat on Debian/Ubuntu
`sudo yum update metricbeat` | Upgrade Metricbeat on CentOS/RHEL
`sudo dnf upgrade metricbeat` | Upgrade Metricbeat on Fedora
`sudo brew upgrade metricbeat` | Upgrade Metricbeat on macOS using Homebrew
`sudo choco upgrade metricbeat` | Upgrade Metricbeat on Windows using Chocolatey

