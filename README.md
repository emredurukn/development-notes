Development Notes
====================
Notes I got while developing software

## PostgreSQL

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
$ DROP DATABASE database_name;          # delete database

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
$ convert image1.jpg image2.jpg +append output_image.jpg     # merge two images
$ convert image1.jpg -resize 150% output_image.jpg           # resize image
$ convert image1.jpg -crop 2x1@ %d.jpg                       # split the image into two. Output -> 0.jpg, 1.jpg
$ convert image1.jpg -crop 3x1@ -scene 3 %d.jpg              # split the image into three with offset. Output -> 3.jpg, 4.jpg, 5.jpg
$ convert *.jpg output.pdf                                   # create pdf from images
$ convert input.pdf %d.jpg                                   # extract images from pdf
```


## Git

```bash
$ git commit --amend -m "an updated commit message"          # change last commit message before push to remote server
```

## Rbenv

```bash
$ rbenv install 2.5.1     # install ruby-build
$ rbenv global 2.5.1      # set ruby-build
$ rbenv versions          # list installed ruby-build
$ rbenv uninstall 2.5.0   # uninstall ruby-build
$ rbenv rehash            # enable changes after gem installation
$ rbenv install -l        # list all versions ruby-build
```

### rbenv zsh integration
```bash
$ echo 'export PATH=$HOME/.rbenv/bin:/usr/local/bin:$HOME/.bin:$PATH' >> ~/.zshenv
$ echo 'eval "$(rbenv init - zsh)"' >> ~/.zshenv
$ echo 'source $HOME/.zshenv' >> ~/.zshrc
$ exec $SHELL
```

### pyenv zsh integration
```bash
$ echo 'eval "$(pyenv init -)"' >> ~/.zshrc
$ exec $SHELL
```

## GnuPG

# encrypt file  (file_name.txt -> file_name.txt.gpg)
gpg -c file_name.txt
 
# decrypt file  (file_name.txt.gpg -> file_name.txt.gpg)
gpg -o file_name.txt -d file_name.txt.gpg