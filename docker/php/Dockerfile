FROM php:8.2.1-fpm

# Non interactive commands
ENV DEBIAN_FRONTEND noninteractive

# Update SO package manager
RUN apt-get update \
    && apt-get install libzip-dev libpng-dev libonig-dev libxml2-dev zip unzip iputils-ping supervisor procps git -y \
    && docker-php-ext-install zip pdo_mysql mbstring xml gd simplexml \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Copy .ini files
COPY *.ini /usr/local/etc/php/conf.d/

# Install composer on container
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /var/www/app
