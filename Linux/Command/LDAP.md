# LDAP Cheat Sheet

LDAP (Lightweight Directory Access Protocol) is a protocol used for accessing and managing directory services. This cheat sheet provides commands and concepts for working with LDAP.

## LDAP Basics

TERM | DESCRIPTION
---|---
DN (Distinguished Name) | A unique identifier for an entry in the directory tree
RDN (Relative Distinguished Name) | The unique identifier for an entry within its parent entry
Attribute | A piece of information associated with an entry (e.g., name, email)
ObjectClass | Defines the set of attributes an entry can have
LDAP URL | A URL that specifies the protocol, host, port, and DN of an LDAP server

## LDAP Operations

COMMAND | DESCRIPTION
---|---
`ldapsearch -x -b <base_dn> <filter>` | Search the directory using a base DN and a filter
`ldapadd -x -D <bind_dn> -w <password> -f <ldif_file>` | Add an entry to the directory using an LDIF file
`ldapmodify -x -D <bind_dn> -w <password> -f <ldif_file>` | Modify an entry in the directory using an LDIF file
`ldapdelete -x -D <bind_dn> -w <password> <dn>` | Delete an entry from the directory using its DN

## LDIF (LDAP Data Interchange Format)

COMMAND | DESCRIPTION
---|---
`dn: <entry_dn>` | Specifies the DN of an entry in an LDIF file
`changetype: add` | Indicates that an entry should be added
`changetype: modify` | Indicates that an entry should be modified
`changetype: delete` | Indicates that an entry should be deleted
`add: <attribute>` | Specifies an attribute to add or modify
`delete: <attribute>` | Specifies an attribute to delete
`replace: <attribute>` | Specifies an attribute to replace

## LDAP Filters

OPERATOR | DESCRIPTION
---|---
`=` | Equal to
`>=` | Greater than or equal to
`<=` | Less than or equal to
`~=` or `=*` | Present (attribute exists)
`!=` | Not equal to
`<=*` | Less than or equal to (lexical order)
`>=*` | Greater than or equal to (lexical order)
`<` | Less than
`>` | Greater than
`~=` or `=*` | Approximate match (e.g., case-insensitive match)
`<` or `>` | Range (e.g., `uidNumber>=1000`)

## LDAP Tools

COMMAND | DESCRIPTION
---|---
`ldapsearch` | Command-line tool to search the directory
`ldapadd` | Command-line tool to add entries to the directory
`ldapmodify` | Command-line tool to modify entries in the directory
`ldapdelete` | Command-line tool to delete entries from the directory
`ldapwhoami` | Command-line tool to authenticate and display the authenticated DN

