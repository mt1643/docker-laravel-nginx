FROM php:8.2-fpm

ENV TZ Asia/Tokyo

RUN apt-get update && \
    apt-get install -y git unzip libzip-dev libicu-dev libonig-dev libfreetype-dev libjpeg62-turbo-dev libpng-dev && \
    docker-php-ext-configure gd --with-freetype --with-jpeg  &&\
    docker-php-ext-install intl pdo_mysql zip bcmath -j$(nproc) gd

COPY ./docker/app/php.ini /usr/local/etc/php/php.ini

COPY --from=composer:2.5.8 /usr/bin/composer /usr/bin/composer

WORKDIR /app
