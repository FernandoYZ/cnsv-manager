FROM php:8.3-fpm-alpine

# Instala dependencias del sistema
RUN apk add --no-cache \
    postgresql-dev \
    libzip-dev \
    zip \
    unzip \
    supervisor \
    nginx

# Instala extensiones PHP
RUN docker-php-ext-install pdo pdo_pgsql pcntl opcache zip

# Instala Composer
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

# Configuración de PHP
COPY docker/php/php.ini /usr/local/etc/php/conf.d/laravel.ini

WORKDIR /var/www/html
