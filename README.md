#Multi environment docker structure

This project is a basic structure for a multi environment docker application for PHP development using Symfony (http://symfony.com/), Composer (https://getcomposer.org/) and xDebug (http://xdebug.org/).

The main objective of this project is to understand how docker (https://www.docker.com/) and docker-compose (https://www.docker.com/docker-compose) works.

It defines two docker-compose.yml files (one docker-compose.yml and one docker-compose.prod.yml), for development and production environment, and two folders containing configuration and docker files for each environment.

##Dependencies
- docker 1.9.1
- docker-compose 1.5.2

##Usage

Using docker-compose:
- In development environment, inside docker directory, execute:
> docker-compose up -d
- In production environment, inside docker directory, execute:
> docker-compose -f docker-compose.prod.yml up -d

##Development environment

The development environment uses the docker-compose.yml file to create five containers:
- data
- mysql
- phpfpm
- nginx
- phpMyAdmin

###The data container

This container just map the source code folder in the host machine (/app/) to the nginx public folder.  

### The mysql container

This container uses the mysql 5.6 oficinal image (https://hub.docker.com/_/mysql/) to create a MySQL container.

The environment variables should be defined in /dev/mysql/mysql.env file (there is a /dev/mysql/mysql.env.example).

The service configuration should be done in /dev/mysql/my.cnf file.

### The phpfpm container

The image is based on phpfpm 5.6.16 oficial image (https://hub.docker.com/_/php/) and is defined in /dev/phpfpm/Dockerfile.

The xdebug listen to the port 9010, but **it was not tested yet**.

The Symfony installer composer and git are installed in this container.

### The nginx container

This container uses nginx 1.9.8 oficial image (https://hub.docker.com/_/nginx/).

The configuration should be done in /dev/nginx/default.conf.

### The phpmyadmin container

This container uses the corbinu/docker-phpmyadmin image (https://hub.docker.com/r/corbinu/docker-phpmyadmin/). It's possible to access phpMyAdmin in port 8181.

##Production environment

The production environment uses the docker-compose.prod.yml file to create four containers:
- data
- mysql
- phpfpm
- nginx

###The data container

Same as development, this container just map the source code folder in the host machine (app/) to the nginx public folder.  

### The mysql container

This container uses the mysql 5.6 oficinal image (https://hub.docker.com/_/mysql/) to create a MySQL container.

The environment variables should be defined in /dev/mysql/mysql.env file (there is a /dev/mysql/mysql.env.example).

The service configuration should be done in /dev/mysql/my.cnf file.


### The phpfpm container

The image is based on phpfpm 5.6.16 oficial image (https://hub.docker.com/_/php/) and is defined in /dev/phpfpm/Dockerfile.

There is no xdebug configured in this image.

The Symfony installer composer and git are installed in this container.

### The nginx container

This container uses nginx 1.9.8 oficial image(https://hub.docker.com/_/nginx/).

The configuration should be done in /dev/nginx/default.conf.
