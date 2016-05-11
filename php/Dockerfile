FROM php:5.6-fpm
MAINTAINER Frederico Wuerges Becker <fred.wuerges@gmail.com>

# PHP.ini
COPY config/php.ini /usr/local/etc/php/

# Install dependencies
RUN apt-get update && \
    apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng12-dev \
        libjpeg-dev \
        libmcrypt-dev \
        libxml2-dev \
        libzzip-dev

# PHP Extensions
RUN docker-php-ext-install mysql && \
    docker-php-ext-install mysqli && \
    docker-php-ext-install pdo && \
    docker-php-ext-install pdo_mysql && \
    docker-php-ext-install mcrypt && \
    docker-php-ext-install mbstring && \
    docker-php-ext-configure gd --with-jpeg-dir=/usr --with-png-dir=/usr --with-freetype-dir=/usr && \
    docker-php-ext-install gd && \
    docker-php-ext-install zip

# PHP-FPM
RUN usermod -u 1000 www-data

# Composer
RUN curl -sS https://getcomposer.org/installer|php

WORKDIR /var/www