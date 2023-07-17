# SELinux Cheat Sheet

SELinux (Security-Enhanced Linux) is a security framework implemented in the Linux kernel. It provides an additional layer of access control and enforces mandatory access control policies to enhance system security.

## SELinux Modes

COMMAND | DESCRIPTION
---|---
`getenforce` | Check the current SELinux mode (Enforcing, Permissive, or Disabled)
`setenforce <Enforcing|Permissive|Disabled>` | Change the SELinux mode temporarily
`sestatus` | Display detailed SELinux status

## SELinux Contexts

COMMAND | DESCRIPTION
---|---
`ls -Z` | List file and directory SELinux contexts
`chcon <context> <file>` | Change the SELinux context of a file or directory
`restorecon -R <directory>` | Restore default SELinux contexts recursively

## SELinux Booleans

COMMAND | DESCRIPTION
---|---
`getsebool -a` | List all SELinux booleans and their current state
`setsebool <boolean> <value>` | Change the value of a SELinux boolean
`semanage boolean -l` | List SELinux booleans and their associated contexts
`semanage boolean -m --<boolean> <value>` | Modify the value of a SELinux boolean permanently

## SELinux Troubleshooting

COMMAND | DESCRIPTION
---|---
`sealert -a /var/log/audit/audit.log` | Analyze SELinux denials from the audit log
`audit2why <audit_log_entry>` | Translate SELinux denial messages into human-readable explanations
`ausearch -m avc -ts recent` | Search for recent SELinux denials in the audit log
`semanage fcontext -l` | List SELinux file contexts

