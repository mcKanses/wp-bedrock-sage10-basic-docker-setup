FROM composer:2.5

RUN apk update && \
    apk add \
        wget \
        libzip-dev \
        zip

RUN docker-php-ext-install zip mysqli pdo pdo_mysql \
    && docker-php-ext-enable pdo_mysql

WORKDIR /app

COPY wordpress/composer.json .
RUN composer install

CMD tail -F anything