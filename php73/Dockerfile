FROM php:7.3-fpm-alpine

RUN apk update; \
    apk upgrade;

RUN apk add --no-cache \
    zlib-dev \
    libzip-dev \
    libmcrypt-dev \
    icu-dev \
    bzip2-dev \
    gettext \
    gettext-dev \
    freetype libpng libjpeg-turbo freetype-dev libpng-dev libjpeg-turbo-dev \
    libxml2-dev;
# For pecl , mongo, xdebug
RUN apk add --update --no-cache --virtual .ext-deps \
    gcc g++ autoconf make openssl-dev;

RUN apk add --no-cache --virtual .mongodb-ext-build-deps;

RUN pecl install xdebug-2.9.4 && \
    pecl install mongodb && \
    pecl install mcrypt &&\
    apk del .mongodb-ext-build-deps && \
    pecl clear-cache && \
    docker-php-ext-enable xdebug && \
    docker-php-ext-enable mongodb && \
    docker-php-ext-enable mcrypt && \
    docker-php-source delete;


RUN docker-php-ext-configure gettext;
RUN docker-php-ext-configure gd \
    --with-freetype-dir=/usr/include/ \
    --with-png-dir=/usr/include/ \
    --with-jpeg-dir=/usr/include/;

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
    gettext \
    gd \
    zip \
    soap;

# RUN apk del gettext-dev libzip-dev bzip2-dev icu-dev zlib-dev;
RUN apk del --no-cache freetype-dev libpng-dev libjpeg-turbo-dev;
RUN rm -rf /var/cache/apk/*;

RUN wget https://phar.phpunit.de/phpunit-9.1.1.phar -O /usr/local/bin/phpunit;
RUN chmod +x /usr/local/bin/phpunit;

# TODO : agregar modulo redis