Development Notes
====================

## Postgresql

```bash
$ psql postgres     # start psql (command line utility for postgresql) 

$ \du    # list users
$ \l     # list databases
$ \q     # close psql

$ CREATE ROLE user_name WITH LOGIN PASSWORD 'password';  # create user
$ ALTER ROLE user_name CREATEDB;    # user authorized to create database

$ psql postgres -U user_name        # start psql with user

$ CREATE DATABASE database_name;    # create database
$ \connect database-name;           # connect database
$ \dl                               # list tables
```