FROM php:fpm-alpine
WORKDIR "/application"

RUN apk update && apk add \
    freetype-dev \
    libpng-dev \
    libjpeg-turbo-dev \
    mysql-client 

RUN docker-php-ext-install -j$(nproc) iconv \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install -j$(nproc) mysqli pdo_mysql
