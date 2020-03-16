FROM php:5.6-fpm-alpine

RUN apk update \
    apk upgrade;

RUN apk add --no-cache \
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
    # pecl install redis && \
    pecl install mongodb && \
    apk del .mongodb-ext-build-deps && \
    pecl clear-cache && \
    docker-php-ext-enable mongodb && \
    docker-php-source delete;

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
    xsl \
    soap \
    gettext;

# RUN apk del build-dependencies && \
RUN rm -rf /var/cache/apk/*