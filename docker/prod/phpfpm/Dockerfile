FROM php:5.6.16-fpm

MAINTAINER Fernando Giovanini <fernando@bdata.it>

# Change to nginx root directory instead of /var/www/html
WORKDIR /usr/share/nginx/html

# Install PHP extensions dependencies
RUN apt-get update;

# Install zip, curl, zlib, PDO MySQL, git
RUN apt-get install -y libmcrypt-dev \
                      libcurl4-gnutls-dev \
                      zlib1g-dev \
                      git \
                      && docker-php-ext-install mcrypt \
                      && docker-php-ext-install curl \
                      && docker-php-ext-install zip \
                      && docker-php-ext-install pdo_mysql;

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Install Symfony3
RUN sudo curl -LsS https://symfony.com/installer -o /usr/local/bin/symfony && chmod a+x /usr/local/bin/symfony
