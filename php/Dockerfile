FROM php:8.2-fpm

RUN echo "deb http://archive.debian.org/debian stretch main" > /etc/apt/sources.list

RUN apt-get update && apt-get install -y \
    zip \
    curl \
    unzip \
    wget \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

RUN docker-php-ext-install opcache fileinfo \
    && pecl install redis \
    && docker-php-ext-enable redis

# 下载Composer安装程序
ENV COMPOSER_HOME /var/www/.composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN ls -alh /usr/local/bin

WORKDIR /var/www
