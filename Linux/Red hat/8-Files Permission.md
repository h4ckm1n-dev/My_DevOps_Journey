# File Permissions Cheat Sheet

Understanding and managing file permissions is crucial for system administration. This cheat sheet provides concepts and commands for managing file and directory permissions, including changing permissions, ownership, and group associations in Linux.

## File Permission Representation

Permission | Symbol | Octal
---|---|---
Read | `r` | 4
Write | `w` | 2
Execute | `x` | 1

## Changing Permissions

COMMAND | DESCRIPTION
---|---
`chmod <permissions> <file>` | Change the permissions of a file
`chmod -R <permissions> <directory>` | Recursively change the permissions of a directory and its contents

## Permission Symbols

Symbol | Description
---|---
`+` | Add permission
`-` | Remove permission
`=` | Set permission explicitly

## Changing Ownership

COMMAND | DESCRIPTION
---|---
`chown <owner> <file>` | Change the owner of a file
`chown <owner>:<group> <file>` | Change the owner and group of a file
`chown -R <owner> <directory>` | Recursively change the owner of a directory and its contents

## Changing Group Associations

COMMAND | DESCRIPTION
---|---
`chgrp <group> <file>` | Change the group ownership of a file
`chgrp -R <group> <directory>` | Recursively change the group ownership of a directory and its contents

## Special Permissions

Permission | Symbol | Octal | Description
---|---|---|---
Setuid | `u+s` | 4000 | Execute with the privileges of the owner
Setgid | `g+s` | 2000 | Execute with the privileges of the group
Sticky | `o+t` | 1000 | Restrict deletion of files in a directory

## Default Permissions (umask)

COMMAND | DESCRIPTION
---|---
`umask` | Display the current umask value
`umask <mask>` | Set the umask value

