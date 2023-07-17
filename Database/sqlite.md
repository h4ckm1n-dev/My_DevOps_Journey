# SQLite Cheat-Sheet

SQLite is a self-contained, serverless, and zero-configuration database engine that is widely used for embedded systems and small-scale applications. It provides a simple and lightweight solution for managing relational databases.

Project Homepage: [SQLite](https://www.sqlite.org/)

## Database Operations

COMMAND | DESCRIPTION
---|---
`sqlite3 <database_file>` | Open or create a SQLite database file
`.databases` | List all attached databases
`.open <database_file>` | Open a specific database file
`.tables` | List all tables in the current database
`.database` | Display the current database name
`.quit` | Exit the SQLite shell

## Table Operations

COMMAND | DESCRIPTION
---|---
`CREATE TABLE <table_name> (<column_definitions>);` | Create a new table with specified columns
`.schema <table_name>` | Display the structure of a table
`DROP TABLE <table_name>;` | Delete a table

## Data Manipulation

COMMAND | DESCRIPTION
---|---
`INSERT INTO <table_name> (<column_list>) VALUES (<value_list>);` | Insert a new row into a table
`SELECT <column_list> FROM <table_name> WHERE <condition>;` | Retrieve data from a table
`UPDATE <table_name> SET <column_name> = <new_value> WHERE <condition>;` | Update data in a table
`DELETE FROM <table_name> WHERE <condition>;` | Delete data from a table

## Querying

COMMAND | DESCRIPTION
---|---
`SELECT * FROM <table_name>;` | Retrieve all rows from a table
`SELECT <column_list> FROM <table_name> ORDER BY <column_name> [ASC/DESC];` | Retrieve data from a table and order the result
`SELECT <column_list> FROM <table_name> LIMIT <count>;` | Retrieve a limited number of rows from a table
`SELECT <column_list> FROM <table_name> WHERE <condition>;` | Retrieve data from a table based on a condition
`SELECT <aggregate_function>(<column_name>) FROM <table_name>;` | Perform an aggregate function (e.g., COUNT, SUM, AVG) on a column

## Importing and Exporting Data

COMMAND | DESCRIPTION
---|---
`.import <file> <table_name>` | Import data from a file into a table
`.output <file>` | Redirect output to a file
`.mode csv` | Set the output mode to CSV
`.mode column` | Set the output mode to aligned columns
`.headers on` | Enable column headers in the output
`.dump <table_name>` | Dump the SQL statements for recreating a table

## Transactions

COMMAND | DESCRIPTION
---|---
`.begin` | Start a new transaction
`.commit` | Commit the current transaction
`.rollback` | Roll back the current transaction

## User and Permission Management

COMMAND | DESCRIPTION
---|---
`.auth ON` | Enable user authentication
`.users` | List all users and their access privileges
`.useradd <username> <password>` | Create a new user
`.userdel <username>` | Delete a user
`.grant <privileges> ON <table_name> TO <username>` | Grant privileges to a user
`.revoke <privileges> ON <table_name> FROM <username>` | Revoke privileges from a user

