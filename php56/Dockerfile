FROM php:5.6-fpm-alpine

RUN apk update \
    apk upgrade;

RUN apk add --no-cache \
    zip libzip-dev \
    icu-dev \
    libmcrypt-dev \
    libxslt-dev \
    gettext \
    gettext-dev;
# For mongodb support
RUN apk add --update --no-cache --virtual .ext-deps \
    gcc g++ autoconf make openssl-dev;
RUN \
    apk add --no-cache --virtual .mongodb-ext-build-deps openssl-dev pcre-dev;
RUN \
    pecl install redis-2.2.8 && \
    pecl install mongodb && \
    pecl install mongo && \
    pecl install xdebug-2.5.5 && \
    apk del .mongodb-ext-build-deps && \
    pecl clear-cache && \
    docker-php-ext-enable redis && \
    docker-php-ext-enable mongodb && \
    docker-php-ext-enable mongo && \
    docker-php-ext-enable xdebug && \
    docker-php-source delete;

RUN docker-php-ext-configure intl \
    && docker-php-ext-configure mcrypt \
    && docker-php-ext-configure pcntl \
    && docker-php-ext-configure gettext \
    && docker-php-ext-configure zip --with-libzip;

RUN docker-php-ext-install \
    mysqli \
    mysql \
    pdo \
    pdo_mysql \
    pcntl \
    mcrypt \
    intl \
    xsl \
    soap \
    zip \
    gettext;

#RUN apk del build-dependencies;
#RUN apk del gcc g++ autoconf make openssl-dev pcre-dev;
#RUN apk del .ext-deps;
RUN apk del gettext-dev;
    # libzip-dev libmcrypt-dev libxslt-dev 
RUN rm -rf /var/cache/apk/*
