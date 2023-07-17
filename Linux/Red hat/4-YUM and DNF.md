# YUM Cheat Sheet

YUM (Yellowdog Updater Modified) is a package management tool used in Red Hat-based Linux distributions. It simplifies the process of managing software packages by automatically resolving dependencies and providing an easy-to-use interface.

## Package Installation

COMMAND | DESCRIPTION
---|---
`yum install <package>` | Install a package
`yum localinstall <package.rpm>` | Install a local RPM package file
`yum groupinstall <group>` | Install a package group

## Package Removal

COMMAND | DESCRIPTION
---|---
`yum remove <package>` | Remove a package
`yum erase <package>` | Remove a package along with its dependencies

## Package Updating

COMMAND | DESCRIPTION
---|---
`yum update` | Update all installed packages
`yum update <package>` | Update a specific package

## Package Searching

COMMAND | DESCRIPTION
---|---
`yum search <keyword>` | Search for packages by keyword
`yum info <package>` | Display detailed information about a package
`yum list` | List all installed packages
`yum list available` | List all available packages
`yum list installed` | List all installed packages
`yum list updates` | List available package updates

## Repository Management

COMMAND | DESCRIPTION
---|---
`yum repolist` | List enabled repositories
`yum repoinfo <repo>` | Display information about a specific repository
`yum-config-manager --enable <repo>` | Enable a repository
`yum-config-manager --disable <repo>` | Disable a repository

DNF (Dandified Yum) is a package manager used in Fedora, CentOS, and other Red Hat-based Linux distributions. It provides a command-line interface for managing software packages. Here's a cheat sheet for DNF commands:

# Dnf Cheat Sheet

## Package Management

|COMMAND|DESCRIPTION|
|---|---|
|`dnf install <package>`|Install a package|
|`dnf remove <package>`|Remove a package|
|`dnf update`|Update all installed packages|
|`dnf upgrade`|Upgrade the system by installing updated packages|
|`dnf search <keyword>`|Search for packages containing a keyword|
|`dnf info <package>`|Display detailed information about a package|
|`dnf list`|List installed packages|
|`dnf repolist`|List enabled repositories|
|`dnf config-manager --add-repo <repo>`|Add a new repository|
|`dnf config-manager --enable <repo>`|Enable a repository|
|`dnf config-manager --disable <repo>`|Disable a repository|

## Repository Management

|COMMAND|DESCRIPTION|
|---|---|
|`dnf repolist`|List enabled repositories|
|`dnf config-manager --add-repo <repo>`|Add a new repository|
|`dnf config-manager --enable <repo>`|Enable a repository|
|`dnf config-manager --disable <repo>`|Disable a repository|

## System Upgrades

|COMMAND|DESCRIPTION|
|---|---|
|`dnf system-upgrade download`|Download packages for a system upgrade|
|`dnf system-upgrade reboot`|Reboot and perform a system upgrade|

## Package Information

|COMMAND|DESCRIPTION|
|---|---|
|`dnf info <package>`|Display detailed information about a package|
|`dnf provides <file>`|Find which package provides a specific file|
|`dnf list installed`|List installed packages|
|`dnf list available`|List available packages|

## Package Group Management

|COMMAND|DESCRIPTION|
|---|---|
|`dnf group list`|List available package groups|
|`dnf group install <group>`|Install a package group|
|`dnf group remove <group>`|Remove a package group|
|`dnf group info <group>`|Display information about a package group|

These commands should help you get started with managing packages and repositories using DNF. Remember to use the appropriate package manager for your Linux distribution, as some commands and options may vary.