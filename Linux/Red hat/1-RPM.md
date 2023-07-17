# RPM Cheat Sheet

RPM (Red Hat Package Manager) is a package management system used in Red Hat-based Linux distributions. It provides a way to install, query, update, and remove software packages in the RPM format.

## Package Installation

COMMAND | DESCRIPTION
---|---
`rpm -i <package.rpm>` | Install an RPM package
`rpm -ivh <package.rpm>` | Install an RPM package with verbose output and progress
`rpm -U <package.rpm>` | Upgrade an RPM package (if already installed)
`rpm -e <package>` | Remove an RPM package

## Querying Packages

COMMAND | DESCRIPTION
---|---
`rpm -qa` | List all installed packages
`rpm -qi <package>` | Display information about an installed package
`rpm -ql <package>` | List files provided by an installed package
`rpm -qd <package>` | List documentation files provided by an installed package
`rpm -qc <package>` | List configuration files provided by an installed package
`rpm -qf <file>` | Find the package that owns a file
`rpm -q --whatrequires <package>` | List packages that require a specific package

## Verifying Packages

COMMAND | DESCRIPTION
---|---
`rpm -V <package>` | Verify the integrity of an installed package
`rpm -Va` | Verify the integrity of all installed packages

## Querying and Verifying Packages (Without Installing)

COMMAND | DESCRIPTION
---|---
`rpm -qip <package.rpm>` | Display information about an RPM package (without installing)
`rpm -qpl <package.rpm>` | List files provided by an RPM package (without installing)
`rpm -qpd <package.rpm>` | List documentation files provided by an RPM package (without installing)
`rpm -qpc <package.rpm>` | List configuration files provided by an RPM package (without installing)
`rpm -q --whatprovides <capability>` | Find the package that provides a specific capability (e.g., a shared library)

