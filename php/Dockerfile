FROM php:8.2-fpm

RUN echo "deb http://archive.debian.org/debian stretch main" > /etc/apt/sources.list

RUN apt-get update && apt-get install -y \
    zip \
    curl \
    unzip \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

RUN docker-php-ext-install opcache fileinfo \
    && pecl install redis \
    && docker-php-ext-enable redis

WORKDIR /var/www
