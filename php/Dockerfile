FROM php:7.4-fpm

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        git \
        curl \
        libmemcached-dev \
        libz-dev \
        libpq-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
        libfreetype6-dev \
        libssl-dev \
        libmcrypt-dev

# Install the PHP pdo_mysql extension
RUN docker-php-ext-install pdo_mysql


# Install the PHP gd library
RUN docker-php-ext-configure gd \
        --with-jpeg \
        --with-freetype && \
    docker-php-ext-install gd

# Install Xdebug
RUN pecl install xdebug && docker-php-ext-enable xdebug
COPY ./xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini

# Install ZIP
RUN pecl install zip && docker-php-ext-enable zip

# Install composer
RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer