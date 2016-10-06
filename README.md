# Rails On Docker

This is a simple project of Docker and Rails for development.

## Requirements

* [Docker for Mac](https://docs.docker.com/docker-for-mac/)

## Application Versions

The application versions in the docker container are the following:

* Ruby 2.2.5
* Rails 5~

## Features

This Docker and Docker Compose settings support the following:

* Persistant database (MySQL)
* Persistant application log files
* Detect file changes from localhost

## Usage

### Start the application

```
$ docker-compose up

$ open http://localhost:3000
```

### Invoke rails commands

For invoking rails commands, you should enter the docker container.

Examples:

```
$ docker-compose exec app bash

root@2987c7ab1b82:/# cd /app
root@2987c7ab1b82:/app# bundle exec rails generate scaffold page name:string title:string
root@2987c7ab1b82:/app# bundle exec rake db:migrate
root@2987c7ab1b82:/app# exit

$ open http://localhost:3000/pages
```

### Connect to the database

```
$ docker-compose exec mysql mysql -uroot -p
Enter password: # The default password is written in docker-compose.yml.

mysql> show databases;
+-----------------------------+
| Database                    |
+-----------------------------+
| information_schema          |
| mysql                       |
| performance_schema          |
| rails-on-docker_development |
| rails-on-docker_test        |
| sys                         |
+-----------------------------+
6 rows in set (0.00 sec)
```
