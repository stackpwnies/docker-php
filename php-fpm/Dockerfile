FROM php:fpm-alpine
WORKDIR "/application"

RUN apk update && apk add \
    freetype-dev \
    libpng-dev \
    libjpeg-turbo-dev \
    mysql-client \
    bzip2-dev \
    libexif-dev \
    gettext-dev \
    icu-dev \
    libxml2-dev \
    libxslt-dev \
    libzip-dev

RUN docker-php-ext-install -j$(nproc) iconv \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install -j$(nproc) mysqli pdo_mysql \
    && docker-php-ext-install -j$(nproc) bcmath bz2 calendar \
    && docker-php-ext-install -j$(nproc) exif gettext intl shmop \
    && docker-php-ext-install -j$(nproc) soap sockets wddx xsl zip \
    && docker-php-ext-enable opcache.so

ADD php-ini-overrides.ini /usr/local/etc/php/conf.d/99-php-ini-overrides.ini

RUN cd /usr/local/etc/php && cp php.ini-production php.ini