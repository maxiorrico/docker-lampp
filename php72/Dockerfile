FROM php:7.2-fpm-alpine

RUN apk update; \
    apk upgrade;

RUN apk add --no-cache \
    zlib-dev \
    libzip-dev \
    icu-dev \
    bzip2-dev;

RUN docker-php-ext-install \
    mysqli \
    bz2 \
    intl \
    iconv \
    bcmath \
    opcache \
    calendar \
    mbstring \
    pdo_mysql \
    zip;
