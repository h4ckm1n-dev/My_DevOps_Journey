# MariaDB Cheat-Sheet

MariaDB is an open-source relational database management system (RDBMS) that is compatible with MySQL. It offers a variety of features and capabilities for managing and querying databases.

Project Homepage: [MariaDB](https://mariadb.org/)

## Database Operations

COMMAND | DESCRIPTION
---|---
`mysql -u <username> -p` | Connect to MariaDB server with specified username
`CREATE DATABASE <database_name>;` | Create a new database
`USE <database_name>;` | Switch to a specific database
`SHOW DATABASES;` | List all databases
`DROP DATABASE <database_name>;` | Delete a database

## Table Operations

COMMAND | DESCRIPTION
---|---
`CREATE TABLE <table_name> (<column_definitions>);` | Create a new table with specified columns
`DESCRIBE <table_name>;` | Display the structure of a table
`SHOW TABLES;` | List all tables in the current database
`DROP TABLE <table_name>;` | Delete a table
`ALTER TABLE <table_name> ADD COLUMN <column_definition>;` | Add a new column to a table
`ALTER TABLE <table_name> DROP COLUMN <column_name>;` | Remove a column from a table

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

## Joins

COMMAND | DESCRIPTION
---|---
`SELECT <column_list> FROM <table1> JOIN <table2> ON <condition>;` | Perform an inner join between two tables
`SELECT <column_list> FROM <table1> LEFT JOIN <table2> ON <condition>;` | Perform a left join between two tables
`SELECT <column_list> FROM <table1> RIGHT JOIN <table2> ON <condition>;` | Perform a right join between two tables

## Indexing

COMMAND | DESCRIPTION
---|---
`CREATE INDEX <index_name> ON <table_name> (<column_name>);` | Create an index on a table column
`SHOW INDEX FROM <table_name>;` | Display the indexes of a table
`ALTER TABLE <table_name> DROP INDEX <index_name>;` | Remove an index from a table

## User and Privilege Management

COMMAND | DESCRIPTION
---|---
`CREATE USER '<username>'@'localhost' IDENTIFIED BY '<password>';` | Create a new user
`GRANT <privileges> ON <database_name>.<table_name> TO '<username>'@'localhost';` | Grant privileges to a user
`REVOKE <privileges> ON <database_name>.<table_name> FROM '<username>'@'localhost';` | Revoke privileges from a user
`FLUSH PRIVILEGES;` | Refresh the privileges

