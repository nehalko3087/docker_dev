FROM php:7.0-fpm

MAINTAINER Kumar Saurabh Sinha "sinha.ksaurabh@gmail.com"

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng12-dev \
        zsh \
        wget \
        git \
        vim \
    && docker-php-ext-install -j$(nproc) iconv mcrypt \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd \
    mbstring \
    mysqli \
    pdo_mysql

COPY ./configuration/php.ini /usr/local/etc/php/php.ini

COPY ./entrypoint/start.sh /usr/local/bin

RUN /usr/local/bin/start.sh
