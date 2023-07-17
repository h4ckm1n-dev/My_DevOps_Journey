# User Management Cheat Sheet

User management is an important aspect of system administration. This cheat sheet provides essential commands for managing user accounts, including user creation, deletion, password management, and user group administration in Linux.

## User Creation and Deletion

COMMAND | DESCRIPTION
---|---
`useradd <username>` | Create a new user account
`userdel <username>` | Delete a user account (without deleting their home directory)
`userdel -r <username>` | Delete a user account along with their home directory

## User Modification and Password Management

COMMAND | DESCRIPTION
---|---
`usermod -l <new_username> <username>` | Change a username
`usermod -c "<new_comment>" <username>` | Change the user's comment (GECOS field)
`passwd <username>` | Set or change a user's password
`passwd -l <username>` | Lock a user account (disable login)
`passwd -u <username>` | Unlock a user account (enable login)

## User Group Management

COMMAND | DESCRIPTION
---|---
`groupadd <groupname>` | Create a new group
`groupdel <groupname>` | Delete a group
`groupmod -n <new_groupname> <groupname>` | Rename a group
`usermod -aG <groupname> <username>` | Add a user to a group
`usermod -g <groupname> <username>` | Change a user's primary group

## User Information and Listing

COMMAND | DESCRIPTION
---|---
`id <username>` | Display user and group information for a specific user
`whoami` | Display the current logged-in username
`users` | List all logged-in users
`w` | Display detailed information about currently logged-in users
`finger <username>` | Display information about a user

