Development Notes
====================
Notes I got while developing software

## Postgresql

```bash
# psql is the command line utility for postgresql

$ psql postgres         # start psql with default database
$ psql database_name    # start psql with other database

$ \du    # list users
$ \l     # list databases
$ \q     # close psql

$ CREATE ROLE user_name WITH LOGIN PASSWORD 'password';  # create user
$ ALTER ROLE user_name CREATEDB;        # user authorized to create database
$ DROP USER user_name;                  # delete user
$ ALTER USER user_name WITH SUPERUSER;  # makes the user super user

$ psql postgres -U user_name            # start psql with user

$ CREATE DATABASE database_name;        # create database
$ \c database-name;                     # connect database
$ \dl                                   # list tables

$ CREATE SCHEMA schema_name;            # create schema
$ CREATE TABLE schema_name.table_name (id integer, password CHAR(10));  # create table
$ INSERT INTO schema_name.table_name values(1, '123456');      # adding data to the table
$ ALTER TABLE schema_name.table_name DROP COLUMN column_name;  # delete column from the table

$ TRUNCATE TABLE table_name;            # reset table
# You can't use truncate command if your table has dependents (another tables that have FK of your table)

$ ALTER SEQUENCE table_name_id_seq RESTART WITH 1;     # reset ids on the table
$ DROP TABLE schema_name.table_name;                   # delete table
```


## ImageMagick

```bash
$ convert 1.jpg 2.jpg +append 3.jpg     # merge two images
```