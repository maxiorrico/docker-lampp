FROM php:5.6-fpm-alpine

RUN apk update \
    apk upgrade;

RUN apk add --no-cache \
    icu-dev \
    libmcrypt-dev \
    gettext \
    gettext-dev;

RUN docker-php-ext-configure intl \
    && docker-php-ext-configure mcrypt \
    && docker-php-ext-configure pcntl \
    && docker-php-ext-configure gettext;

RUN docker-php-ext-install \
    mysqli \
    mysql \
    pdo \
    pdo_mysql \
    pcntl \
    mcrypt \
    intl \
    gettext;
