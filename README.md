# Development Notes

Development notes for for daily uses

## Conda

| Effect                                       | Command                                         |
| -------------------------------------------- | ------------------------------------------------|
| create new environment which uses python 3.6 | `conda create -n myenv python=3.6`              |
| install package                              | `conda install -n myenv tensorflow`             |
| update package                               | `conda update -n myenv tensorflow`              |
| update all packages                          | `conda update --all`                            |
| activate env                                 | `conda activate myenv`                          |
| deactivate current env                       | `conda deactivate`                              |
| list envs                                    | `conda info --envs`                             |
| list packages                                | `conda list -n myenv`                           |
| remove package                               | `conda remove -n myenv tensorflow`              |
| remove environment                           | `conda env remove -n myenv`                     |
| save packages for future use                 | `conda list --export > package-list.txt`        |
| create requirements.txt file                 | `pip freeze > requirements.txt`                 |
| reinstall packages from an export file       | `conda create -n myenv --file package-list.txt` |
| save environment info in a yaml file         | `conda env export > environment.yml`            |
| recreate environment with a yaml file        | `conda env create -f environment.yml`           |


## PostgreSQL

| Effect                             | Command                                                                |
| ---------------------------------- | ---------------------------------------------------------------------- |
| start psql with default database   | `psql postgres`                                                        |
| start psql with other database     | `psql database_name`                                                   |
| list users                         | `\du`                                                                  |
| list databases                     | `\l`                                                                   |
| close psql                         | `\q`                                                                   |
| create user                        | `CREATE ROLE user_name WITH LOGIN PASSWORD 'password';`                |
| user authorized to create database | `ALTER ROLE user_name CREATEDB;`                                       |
| delete user                        | `DROP USER user_name;`                                                 |
| makes the user super user          | `ALTER USER user_name WITH SUPERUSER;`                                 |
| start psql with user               | `psql postgres -U user_name`                                           |
| create database                    | `CREATE DATABASE database_name;`                                       |
| connect database                   | `\c database_name;`                                                    |
| list tables                        | `\dl`                                                                  |
| delete database                    | `DROP DATABASE database_name;`                                         |
| create schema                      | `CREATE SCHEMA schema_name;`                                           |
| create table                       | `CREATE TABLE schema_name.table_name (id integer, password CHAR(10));` |
| adding data to the table           | `INSERT INTO schema_name.table_name values(1, '123456');`              |
| delete column from the table       | `ALTER TABLE schema_name.table_name DROP COLUMN column_name;`          |
| reset table                        | `TRUNCATE TABLE table_name;`                                           |
| reset ids on the table             | `ALTER SEQUENCE table_name_id_seq RESTART WITH 1;`                     |
| delete table                       | `DROP TABLE schema_name.table_name;`                                   |


## ImageMagick

| Effect                                                                | Command                                                  |
| --------------------------------------------------------------------- | -------------------------------------------------------- |
| merge two images                                                      | `convert image1.jpg image2.jpg +append output_image.jpg` |
| resize image                                                          | `convert image1.jpg -resize 150% output_image.jpg`       |
| split the image into two. Output -> 0.jpg, 1.jpg                      | `convert image1.jpg -crop 2x1@ %d.jpg`                   |
| split the image into three with offset. Output -> 3.jpg, 4.jpg, 5.jpg | `convert image1.jpg -crop 3x1@ -scene 3 %d.jpg`          |
| create pdf from images                                                | `convert \*.jpg output.pdf`                              |
| extract images from pdf                                               | `convert input.pdf %d.jpg`                               |


## Git

```bash
$ git commit --amend -m "an updated commit message"     # change last commit message
$ git reset --soft HEAD~1                               # undo last commit
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

## Nvm

```bash
$ nvm ls-remote                 # lists all of the available versions of NodeJs & iojs
$ nvm ls                        # list locally installed version
$ nvm install 12.13.1           # install the version 12.13.1
$ nvm use 12.13.1               # switch to and use the installed 12.13.1 version
$ nvm alias default 12.13.1     # set 12.13.1 as default
$ nvm uninstall 12.13.1         # uninstall node version (cannot uninstall currently-active node version)
```

## rbenv, nvm and anaconda zsh integration with .zshrc

```bash
# nvm
export NVM_DIR="$HOME/.nvm"
[ -s "/usr/local/opt/nvm/nvm.sh" ] && . "/usr/local/opt/nvm/nvm.sh"

# rbenv
export PATH="$HOME/.rbenv/bin:$PATH"
eval "$(rbenv init -)"

# anaconda
__conda_setup="$(CONDA_REPORT_ERRORS=false '/anaconda3/bin/conda' shell.bash hook 2> /dev/null)"
if [ $? -eq 0 ]; then
    \eval "$__conda_setup"
else
    if [ -f "/anaconda3/etc/profile.d/conda.sh" ]; then
        . "/anaconda3/etc/profile.d/conda.sh"
        CONDA_CHANGEPS1=false conda activate base
    else
        \export PATH="/anaconda3/bin:$PATH"
    fi
fi
unset __conda_setup
```


## GnuPG

```bash
$ gpg -c file_name.txt                        # encrypt file  (file_name.txt -> file_name.txt.gpg)
$ gpg -o file_name.txt -d file_name.txt.gpg   # decrypt file  (file_name.txt.gpg -> file_name.txt.gpg)
```

## Mac Command Line Developer Tools

```bash
$ xcode-select --install
```
