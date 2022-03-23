FROM php:8.0.3-alpine

RUN apk add --no-cache \
    wget \
    curl \
    shadow \
    build-base \
    autoconf \
    libxml2-dev \
    zlib-dev \
    libevent \
    libevent-dev \
    openssl-dev \
    gmp-dev \
    icu-dev

RUN docker-php-ext-install \
        pcntl \
        pdo \
        pdo_mysql \
        tokenizer \
        xml \
        sockets \
        gmp \
        bcmath \
        intl

        # Libevent
RUN pecl install event

RUN apk update

# Cleanup
# apk del .build-deps && \
RUN rm -rf /var/cache/apk/* && \
    rm -rf /tmp/*

RUN mkdir -p /var/www

RUN groupmod -g 1000 www-data && \
    usermod -u 1000 www-data

USER www-data

WORKDIR /var/www/html

EXPOSE 6001

CMD ["php", "artisan", "websockets:serve"]