FROM php:8.1-fpm

RUN apt-get update -y && \
    apt-get install -y \
        wget \
        libzip-dev \
        zip

RUN docker-php-ext-install zip mysqli pdo pdo_mysql \
    && docker-php-ext-enable pdo_mysql

RUN docker-php-ext-install mysqli && docker-php-ext-enable mysqli

# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

WORKDIR /app

# Add user for laravel application
# RUN useradd -u 1000 -ms /bin/bash -g www-data www-data

# Copy existing application directory contents
COPY wordpress/. /app/.

# # Copy existing application directory permissions
# COPY --chown=www-data:www-data . /app

# # Change current user to www
# USER www-data

# -R allow php-fpm as root
CMD  /bin/bash -c "\
  php-fpm \
"